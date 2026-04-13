# Домашнее задание: Система мониторинга Zabbix hw-02

**Выполнил:** Сыч Кирилл  
**Дата:** 14 апреля 2026

---

## Задание 1: Установка Zabbix Server

### ✅ Установлено и настроено

- Zabbix Server 7.4 на Debian 13
- PostgreSQL (база данных)
- Apache + PHP 8.4 (веб-интерфейс)
- IP адрес сервера: `10.0.3.4`
  
### 📸 Админ панель

![Hosts](https://github.com/sychnepticaowl-spec/hv-02-Sych-Kirill/blob/main/screenshots/admin-login.png?raw=true) 

### 📋 Команды установки

```bash
# Установка репозитория Zabbix 7.4
wget https://repo.zabbix.com/zabbix/7.4/release/debian/pool/main/z/zabbix-release/zabbix-release_latest_7.4+debian13_all.deb
sudo dpkg -i zabbix-release_latest_7.4+debian13_all.deb
sudo apt update

# Установка Zabbix Server
sudo apt i…R zabbix WITH PASSWORD 'zabbix';
CREATE DATABASE zabbix WITH OWNER zabbix ENCODING 'UTF8' LC_COLLATE='en_US.UTF-8' LC_CTYPE='en_US.UTF-8' TEMPLATE=template0;
EOF

# Импорт схемы
zcat /usr/share/zabbix/sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix

# Настройка пароля
sudo sed -i 's/^# DBPassword=/DBPassword=zabbix/' /etc/zabbix/zabbix_server.conf

# Запуск служб
sudo systemctl restart zabbix-server zabbix-agent2 apache2
sudo systemctl enable zabbix-server zabbix-agent2 apache2
```


## Задание 2: Установка Zabbix Agent

### 📸 Конфигурация хостов

![Hosts](https://github.com/sychnepticaowl-spec/hv-02-Sych-Kirill/blob/main/screenshots/hosts-config.png?raw=true)

### 📸 Лог агента

![Agent Log](https://github.com/sychnepticaowl-spec/hv-02-Sych-Kirill/blob/main/screenshots/agent-log.png?raw=true)

### 📸 Последние данные

![Latest Data](https://github.com/sychnepticaowl-spec/hv-02-Sych-Kirill/blob/main/screenshots/latest-data.png?raw=true)
