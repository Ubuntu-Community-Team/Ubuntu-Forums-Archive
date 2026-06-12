---
title: "Apache2 php.ini adn cli php.ini"
date: 2009-01-13
forum: General Help
---

### Post by chrislynch8 on 2009-01-13
Hello,

My webserver is running fine and I'm running a CRM on it. My php.ini file is in /etc/php5/apache2/php.ini.

For the CRM I have a script called cron.php that I have to call from command line in a cronjob - bu my cli php is using /etc/php5/cli/pnp.ini for configuration.

Can I just remove the cli pnp.ini and create a symbolic link from /etc/php5/apache2/php.ini to /etc/php5/cli

Rgds
Chris

---

### Post by chrislynch8 on 2009-01-13
Hello,

My webserver is running fine and I'm running a CRM on it. My php.ini file is in /etc/php5/apache2/php.ini.

For the CRM I have a script called cron.php that I have to call from command line in a cronjob - bu my cli php is using /etc/php5/cli/pnp.ini for configuration.

Can I just remove the cli pnp.ini and create a symbolic link from /etc/php5/apache2/php.ini to /etc/php5/cli

Rgds
Chris

---

