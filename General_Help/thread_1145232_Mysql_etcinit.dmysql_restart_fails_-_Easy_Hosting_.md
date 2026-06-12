---
title: "Mysql /etc/init.d/mysql restart fails - Easy Hosting Control Panel install"
date: 2009-05-01
forum: General Help
---

### Post by xjairusx on 2009-05-01
Hi everyone,

While in the process of transporting data from one database to my new ovh dedicated server the mysql server seems to have crashed and it lost connection.

Using terminal when I try to restart mysql i'm having no joy.

Can anyone help!?

It says ok to stopping the mysql service but comes up with fail when it tries to restart the mysql service. Any ideas? I can't seem to see any syslog info, the ones I found in /var/log don't seem to contain anything. Hmmm.

---

### Post by xjairusx on 2009-05-01
Ok... I just tried again and it now restarts but i'm still unable to connect to the server using navicat or phpmyadmin.


Update:

Now I can reconnect if i completely close the connection and start again. But for some reason when transferring it doesn't like something and seems to disconnect and block out connections. And when trying to resume it just won't reconnect. Anyone have any ideas on this crazy thing? Its a large database which is 132mb when dumped to an sql file. Alternatively is there any other way to import this data? phpmyadmin doesn't seem any better! I could try upping my max upload limit etc to 200mb I suppose?

```
[Msg] [Dtf] Get table data for: ps_connections_page
[Msg] [Dtf] Start transfer to Target Server: ps_connections_page
[Err] [Dtf] 2013 - Lost connection to MySQL server during query With statement: INSERT INTO `ps_connections_page` VALUES ('50', '9', '2008-12-08 14:48:34', null), ('48', '9', '2008-12-08 14:48:36', null), ('50', '25', '2008-12-08 14:49:15', null), ('50', '9', '2008-12-08 14:49:16', null), ('50', '9', '2008-12-08 14:49:20', null), ('48', '9', '2008-12-08 14:49:24', null), ('0', '31', '2008-12-08 14:49:26', null), ('50', '393', '2008-12-08 14:49:41', null), ('50', '9', '2008-12-08 14:49:42', null), ('50', '9', '2008-12-08 14:49:44', null), ('48', '9', '2008-12-08 14:49:45', null), ('50', '260', '2008-12-08 14:49:47', null), ('50', '9', '2008-12-08 14:49:48', null), ('50', '9', '2008-12-08 14:49:49', null), ('0', '1793', '2008-12-08 14:49:52', null), ('0', '464', '2008-12-08 14:49:53', null), ('48', '9', '2008-12-08 14:49:56', null), ('50', '260', '2008-12-08 14:50:10', null), ('50', '9', '2008-12-08 14:50:11', null), ('48', '9', '2008-12-08 14:50:17', null), ('50', '390', '2008-12-08 14:50:26', null), ('50', '9', '2008-12-08 14:50:27', null), ('50', '9', '2008-12-08 14:50:28', null), ('50', '488', '2008-12-08 14:50:33', null), ('48', '9', '2008-12-08 14:50:33', null), ('50', '9', '2008-12-08 14:50:34', null), ('48', '9', '2008-12-08 14:50:38', null), ('0', '1794', '2008-12-08 14:50:41', null), ('50', '393', '2008-12-08 14:51:22', null), ('50', '9', '2008-12-08 14:51:23', null), ('50', '9', '2008-12-08 14:51:25', null), ('48', '9', '2008-12-08 14:51:27', null), ('0', '1795', '2008-12-08 14:54:25', null), ('0', '839', '2008-12-08 14:54:50', null), ('50', '390', '2008-12-08 14:55:23', null), ('50', '9', '2008-12-08 14:55:24', null), ('50', '6', '2008-12-08 14:55:24', null), ('50', '632', '2008-12-08 14:55:25', null), ('50', '9', '2008-12-08 14:55:26', null), ('50', '9', '2008-12-08 14:55:27', null), ('50', '632', '2008-12-08 14:55:31', null), ('50', '9', '2008-12-08 14:55:33', null), ('48', '9', '2008-12-08 14:55:34', null), ('50', '9', '2008-12-08 14:55:38', null), ('0', '1796', '2008-12-08 14:55:40', null), ('48', '9', '2008-12-08 14:55:44', null), ('50', '632', '2008-12-08 14:55:44', null), ('50', '9', '2008-12-08 14:55:46', null), ('48', '9', '2008-12-08 14:55:49', null), ('50', '372', '2008-12-08 14:55:55', null), ('50', '9', '2008-12-08 14:55:56', null), ('50', '9', '2008-12-08 14:55:57', null), ('48', '9', '2008-12-08 14:56:05', null), ('0', '1222', '2008-12-08 14:56:05', null), ('50', '92', '2008-12-08 14:56:13', null), ('50', '9', '2008-12-08 14:56:14', null), ('50', '9', '2008-12-08 14:56:15', null), ('48', '9', '2008-12-08 14:56:21', null), ('50', '92', '2008-12-08 14:56:23', null), ('50', '9', '2008-12-08 14:56:25', null), ('48', '9', '2008-12-08 14:56:32', null), ('50', '9', '2008-12-08 14:56:33', null), ('0', '311', '2008-12-08 14:56:55', null), ('0', '670', '2008-12-08 14:57:20', null), ('48', '9', '2008-12-08 14:57:41', null), ('0', '1797', '2008-12-08 14:58:11', null), ('0', '1076', '2008-12-08 14:59:24', null), ('0', '712', '2008-12-08 15:00:39', null), ('0', '1798', '2008-12-08 15:01:04', null), ('0', '1799', '2008-12-08 15:01:36', null), ('0', '1800', '2008-12-08 15:01:56', null), ('0', '1801', '2008-12-08 15:02:18', null), ('0', '135', '2008-12-08 15:02:43', null), ('0', '1802', '2008-12-08 15:03:09', null), ('0', '1803', '2008-12-08 15:03:33', null), ('0', '1804', '2008-12-08 15:03:58', null), ('0', '1805', '2008-12-08 15:04:49', null), ('0', '1688', '2008-12-08 15:04:56', null), ('0', '1806', '2008-12-08 15:05:39', null), ('0', '1077', '2008-12-08 15:06:03', null), ('0', '1093', '2008-12-08 15:06:28', null), ('0', '1807', '2008-12-08 15:06:39', null), ('0', '1808', '2008-12-08 15:07:05', null), ('0', '311', '2008-12-08 15:07:18', null), ('0', '927', '2008-12-08 15:07:36', null), ('0', '1809', '2008-12-08 15:07:43', null), ('0', '1810', '2008-12-08 15:08:33', null), ('0', '712', '2008-12-08 15:08:38', null), ('0', '1811', '2008-12-08 15:08:58', null), ('0', '925', '2008-12-08 15:09:08', null), ('0', '457', '2008-12-08 15:09:22', null), ('0', '263', '2008-12-08 15:09:39', null), ('0', '263', '2008-12-08 1
[Err] [Dtf] Terminated 
```

---

