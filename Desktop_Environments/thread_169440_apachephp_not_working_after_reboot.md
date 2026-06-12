---
title: "apache/php not working after reboot"
date: 2006-05-02
forum: Desktop Environments
---

### Post by 4tro on 2006-05-02
topic pretty much says it all...
i can't access my phpsysinfo anymore after a system reboot...
i heard about this problem from another guy but he still hasn't got it fixed
so i'm a little bit in the dark of what's going on here :S
apache still runs though... ( i think)

---

### Post by cgjones on 2006-05-02
Have you rebooted the computer before and not had this problem?

---

### Post by 4tro on 2006-05-02
[quote=cgjones]Have you rebooted the computer before and not had this problem?[/quote]

this was the first reboot since i installed ubuntu

---

### Post by cgjones on 2006-05-02
My thought was that maybe Apache wasn't set up to start when the computer boots. I can't think of the command right off the top of my head, and I don't currently have a computer running Ubuntu to look at. To get Apache running for now, try this:
```

apachectl start

```

---

### Post by 4tro on 2006-05-03
it was allready running
i'm pretty sure that it's php which is acting ****** up...

---

### Post by 4tro on 2006-05-03
maybe it would be a good idea to tell that reinstalling apache, php and phpsysinfo doesn't seem to work...

just a short part of the file my FF tries to download if i open phpsysinfo
> 
addError('include(class.' . PHP_OS . '.php.inc)' , PHP_OS . ' is not currently supported', __LINE__, __FILE__ ); }  if (!extension_loaded('xml')) {   $error->addError('extension_loaded(xml)', 'phpsysinfo requires the xml module for php to work', __LINE__, __FILE__); }  if (!extension_loaded('pcre')) {   $error->addError('extension_loaded(pcre)', 'phpsysinfo requires the pcre module for php to work', __LINE__, __FILE__); }   if (!file_exists(APP_ROOT . '/config.php')) {   $error->addError('file_exists(config.php)', 'config.php does not exist in the phpsysinfo directory.', __LINE__, __FILE__); } else {    require_once(APP_ROOT . '/config.php');             // get the config file }  if ( !empty( $sensor_program ) ) {   $sensor_program = basename( $sensor_program );   if( !file_exists( APP_ROOT . '/includes/mb/class.' . $sensor_program . '.inc.php' ) ) {     $error->addError('include(class.' . htmlspecialchars($sensor_program,

very much looks like php isn't working at all

---

### Post by 4tro on 2006-05-03
okay problem is fixed now...
uninstalled everything i could find of apache, apache2 and php stuff
and installed apache2 and php5 stuff
and simply placed newest phpsysinfo in /var/www/
=)
maybe the package should be updated or something

---

