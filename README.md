# Установка кластера Cassandra через docker-compose
#### 1. Клонируем репозиторий

```shell
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY
```

#### 2. Переименовываем .env.example -> .env

#### 3. Запускаем docker-compose 
```shell
docker compose up -d
```

*Можете использовать флаг -f для явного указания пути docker-file.yml*
```shell
docker compose -f <docker-compose-file> up [OPTIONS] [SERVICE...]
```

![Image alt](https://github.com/sutirick/docker-compose-for-uno/raw/assets/./20241120154502.png)
Видим, что все стартануло успешно.

#### 4. Проверяем локально

```shell
docker ps -a
docker network inspect <nerwork name or network_id>
```

![[Pasted image 20241120152220.png]]

![[Pasted image 20241120152327.png]]

```shell
docker logs cassandra1
```

Увидим, что все завелось корректно
![[Pasted image 20241120152708.png]]

```shell
docker exec -it cassandra1

SELECT <columns | *> FROM system.local
```

![[Pasted image 20241120153347.png]]
*Информация о текущем состоянии данной ноды*

```shell
SELECT <columns | *> FROM system.peers
```

![[Pasted image 20241120153801.png]]
*Информация о других нодах в кластере*

#### 5.Установим cqlsh на другой ПК

```shell
pip install cqlsh [--break-system-packages]
```

#### 6.Проверим подключение ко всем нодам кластера

![[Pasted image 20241120154143.png]]

### Спасибо за внимание