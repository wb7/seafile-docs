# Clean Database

## Seahub

### Session

Since version 5.0, we offered command to clear expired session records in Seahub database.

    cd <install-path>/seafile-server-latest
    ./seahub.sh clearsessions

### Activity

To clean the activity records, login in to MySQL/MariaDB and use the following command:

    use seahub_db;
    DELETE FROM Event WHERE to_days(now()) - to_days(timestamp) > 90;

The corresponding items in UserEvent will deleted automatically by MariaDB when the foreign keys in Event table are deleted.

### Login

To clean the login records, login in to MySQL/MariaDB and use the following command:

    use seahub_db;
    DELETE FROM sysadmin_extra_userloginlog WHERE to_days(now()) - to_days(login_date) > 90;

### File Access

To clean the file access records, login in to MySQL/MariaDB and use the following command:

    use seahub_db;
    DELETE FROM FileAudit WHERE to_days(now()) - to_days(timestamp) > 90;

### File Update

To clean the file update records, login in to MySQL/MariaDB and use the following command:

    use seahub_db;
    DELETE FROM FileUpdate WHERE to_days(now()) - to_days(timestamp) > 90;

### Permisson

To clean the permisson records, login in to MySQL/MariaDB and use the following command:

    use seahub_db;
    DELETE FROM PermAudit WHERE to_days(now()) - to_days(timestamp) > 90;

