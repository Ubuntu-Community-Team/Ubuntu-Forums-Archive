---
title: "How to make a command to auto run as root?"
date: 2009-05-18
forum: General Help
---

### Post by TE0I0TEJIb on 2009-05-18
Hello,
I have to run a command "ubudsldaemon" **as root** on startup, how to make this?

---

### Post by mb_webguy on 2009-05-18
You need to write a script calling the command, and place the script in the /etc/init.d/ directory.  Then use the command "sudo update-rc.d *script_name* defaults" to add the service.

If you later want to remove the service, delete the script and run the command "sudo update-rc.d *script_name* remove".

---

### Post by TheExplorer on 2009-05-18
&#1043;&#1099;, &#1090;&#1077;&#1092;&#1090;&#1077;&#1083;&#1103; :) &#1050;&#1089;&#1090;&#1072;&#1090;&#1080; &#1095;&#1090;&#1086; &#1090;&#1072;&#1084; &#1089; &#1092;&#1086;&#1088;&#1091;&#1084;&#1086;&#1084; &#1088;&#1091;&#1089;&#1089;&#1082;&#1080;&#1084;? &#1051;&#1105;&#1075; &#1086;&#1082;&#1086;&#1085;&#1095;&#1072;&#1090;&#1077;&#1083;&#1100;&#1085;&#1086;? :(

P.S. Sorry that was in Russian. This guy is Russian and our official Ubuntu forum has been down for two weeks already :(

---

### Post by TE0I0TEJIb on 2009-05-18
> **mb_webguy said:**
> You need to write a script calling the command, and place the script in the /etc/init.d/ directory.  Then use the command "sudo update-rc.d *script_name* defaults" to add the service.

If you later want to remove the service, delete the script and run the command "sudo update-rc.d *script_name* remove".

I made everything as you write, but nothing happens on startup, so, I think, the programm starts not as root, maybe I have to type "sudo *command*"?

> **TheExplorer said:**
> &#1043;&#1099;, &#1090;&#1077;&#1092;&#1090;&#1077;&#1083;&#1103; :) &#1050;&#1089;&#1090;&#1072;&#1090;&#1080; &#1095;&#1090;&#1086; &#1090;&#1072;&#1084; &#1089; &#1092;&#1086;&#1088;&#1091;&#1084;&#1086;&#1084; &#1088;&#1091;&#1089;&#1089;&#1082;&#1080;&#1084;? &#1051;&#1105;&#1075; &#1086;&#1082;&#1086;&#1085;&#1095;&#1072;&#1090;&#1077;&#1083;&#1100;&#1085;&#1086;? :(

P.S. Sorry that was in Russian. This guy is Russian and our official Ubuntu forum has been down for two weeks already :(

&#1103; &#1085;&#1077; &#1079;&#1085;&#1072;&#1102;, &#1095;&#1090;&#1086; &#1089; &#1085;&#1080;&#1084; &#1080; &#1082;&#1086;&#1075;&#1076;&#1072; &#1086;&#1090;&#1082;&#1088;&#1086;&#1102;&#1090; &#1089;&#1085;&#1086;&#1074;&#1072;, &#1084;&#1086;&#1075;&#1083;&#1080; &#1073;&#1099; &#1085;&#1072;&#1087;&#1080;&#1089;&#1072;&#1090;&#1100; &#1093;&#1086;&#1090;&#1103;&#1073; &#1095;&#1090;&#1086; &#1091; &#1085;&#1080;&#1093; &#1090;&#1072;&#1084; &#1087;&#1088;&#1086;&#1080;&#1079;&#1086;&#1096;&#1083;&#1086;

---

### Post by TheExplorer on 2009-05-18
> **TE0I0TEJIb said:**
> I made everything as you write, but nothing happens on startup, so, I think, the programm starts not as root, maybe I have to type "sudo *command*"?

No, you don't have to. You input sudo only to update the rc.d. It is intended for the scripts to be run as root. Tell us what script do you want to be autorun and post the script itself here.

P.S. Did you make the script executable?

---

### Post by TE0I0TEJIb on 2009-05-18
> **TheExplorer said:**
> No, you don't have to. You input sudo only to update the rc.d. It is intended for the scripts to be run as root. Tell us what script do you want to be autorun and post the script itself here.

P.S. Did you make the script executable?

i have made the script executable
there is only one line in the script:
```
ubudsldaemon
```
it have to run program, named ubudsldaemon
the script is named ubudsldaemon
"sudo /etc/init.d/ubudsldaemon" works fine and run this prog
i used "sudo update-rc.d ubudsldaemon defaults" and it worked fine

---

### Post by 3rdalbum on 2009-05-18
Why not put the command into /etc/rc.local, just before the "exit" line? All commands in that file are automatically run as root just after the X server starts up.

---

### Post by TE0I0TEJIb on 2009-05-18
> **3rdalbum said:**
> Why not put the command into /etc/rc.local, just before the "exit" line? All commands in that file are automatically run as root just after the X server starts up.

that doesnt work!but in this file there is this:
```
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script **does nothing**.
```
so i need to change execution bits, what is this?the file is executable
this is how the file look like whithout lines with #:
```
ubudsldaemon
exit 0
```

---

### Post by TheExplorer on 2009-05-18
Fire up 'mc', highlight this file and press 'Ctrl+x and then 'c' immediately. You'll be given a lot of options like execution bits, file permissions etc. So make it an executable by ticking with your space bar the appropriate checkboxes :)

P.S. Btw the file should executable by default.

---

### Post by Sidewinder1 on 2009-05-18
Quick question TheExplorer, what is "mc"?
TIA,
Side

---

### Post by TE0I0TEJIb on 2009-05-18
> **Sidewinder1 said:**
> Quick question TheExplorer, what is "mc"?
TIA,
Side

Midnight Commander, r smth like this, it is file manager,  to install it run ```
sudo apt-get install mc
```
but I can make file executable with Dolphin r thru Konsole
but ill try

---

### Post by Yellow Pasque on 2009-05-18
```
sudo chmod +x /etc/rc.local
```

---

### Post by Sidewinder1 on 2009-05-18
Thank you :-)

---

### Post by TE0I0TEJIb on 2009-05-18
> **TheExplorer said:**
> Fire up 'mc', highlight this file and press 'Ctrl+x and then 'c' immediately. You'll be given a lot of options like execution bits, file permissions etc. So make it an executable by ticking with your space bar the appropriate checkboxes :)

P.S. Btw the file should executable by default.
> **Temüjin said:**
> ```
sudo chmod +x /etc/rc.local
```

the file was executable by default, so this doesnt help(

---

### Post by Yellow Pasque on 2009-05-18
Hmm, a link to rc.local script should exist in rc2.d (S99rc.local)

Does rc.local execute correctly when you run this?:
```
sudo /etc/init.d/rc.local start
```
Note: If you want to test the rc.local file without starting the daemon many times, comment that line out for now and use this for testing:
```
echo Hello
```

---

### Post by TE0I0TEJIb on 2009-05-18
> **Temüjin said:**
> Hmm, a link to rc.local script should exist in rc2.d (S99rc.local)

Does rc.local execute correctly when you run this?:
```
sudo /etc/init.d/rc.local start
```
Note: If you want to test the rc.local file without starting the daemon many times, comment that line out for now and use this for testing:
```
echo Hello
```

it works fine and starts daemon!

---

### Post by Yellow Pasque on 2009-05-18
> **TE0I0TEJIb said:**
> it works fine and starts daemon!
Does this help?
```
sudo update-rc.d rc.local defaults 99 01
```

---

### Post by TE0I0TEJIb on 2009-05-19
> **Temüjin said:**
> Does this help?
```
sudo update-rc.d rc.local defaults 99 01
```

hm, this is very strange:
```
gooseman@gooseman:~$ sudo update-rc.d rc.local defaults 99 01
[sudo] password for gooseman:
 System startup links for /etc/init.d/rc.local already exist.

```

How to make script, that will open "sudo ubudsldaemon" in Konsole?

---

