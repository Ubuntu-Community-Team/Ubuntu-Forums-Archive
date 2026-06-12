---
title: "Uninstall .bin package- Google earth"
date: 2009-05-25
forum: General Help
---

### Post by mouratos1a on 2009-05-25
Dear all,
I have seen a similar thread but it did not give me the solution to my problem so here I am ...
I have Ubuntu 9.04
I wanted to install Google Earth 4.3
At the beginning installetion did not want to start so I found that
chmod 755 googleearth-linux-plus-4.3.7284.3916.bin could help...
then installation worked fine...
Since I have an old computer with lazy slow Graphics card Google earth runs (!) very slow...So I decided to unistall..
I did ./uninstall
but received: Could not find a usable uninstall program. Aborting.
I suspect the problem was the change in permissions .
How can I uninstall it anyway ???
Thank you in advance for the help...
Mouratos

---

### Post by Soul-Sing on 2009-05-25
```
cd ~/google-earth sh uninstall
```

or

Move to your Installation Directory where you Installed Google Earth.Remeber by default directory is /home/<username>/google-earth

cd /home/yourename/google-earth

2.Now Execute Following Command

sh uninstall

---

### Post by mouratos1a on 2009-05-25
This is what I have tried together with the results...
lampros@ubuntu:~$ sh uninstall
sh: Can't open uninstall
lampros@ubuntu:~$ sudo sh /opt/google-earth/uninstall
Could not find a usable uninstall program. Aborting.
lampros@ubuntu:~$ cd ~/google-earth sh uninstall
bash: cd: /home/lampros/google-earth: No such file or directory
lampros@ubuntu:~$ cd opt/google-earth sh uninstall
bash: cd: opt/google-earth: No such file or directory
lampros@ubuntu:~$ cd opt/google-earth sh uninstall
bash: cd: opt/google-earth: No such file or directory
lampros@ubuntu:~$ cd opt/google-earth
bash: cd: opt/google-earth: No such file or directory
lampros@ubuntu:~$ cd /opt/google-earth sh uninstall
lampros@ubuntu:/opt/google-earth$ cd /opt/google-earth sh uninstall
lampros@ubuntu:/opt/google-earth$ sh uninstall
Could not find a usable uninstall program. Aborting.
lampros@ubuntu:/opt/google-earth$ 
Although I can see the uninstall file in the /opt/google-earth directory...
Thanks for the tip anyway

---

### Post by Soul-Sing on 2009-05-25
Strange.....

Maybe this will do:

```
sudo rm -rf /opt/google-earth && sudo rm /usr/share/mime/application/vnd.google-earth.* /usr/share/mimelnk/application/vnd.google-earth.* /usr/share/applnk/Google-googleearth.desktop /usr/share/mime/packages/googleearth-mimetypes.xml /usr/share/gnome/apps/Google-googleearth.desktop /usr/share/applications/Google-googleearth.desktop /usr/local/bin/googleearth
```

or: ```
sudo -i -
cd /opt/google-earth/
export DISPLAY=:0
./uninstall
```

---

### Post by mouratos1a on 2009-05-26
Thank you for your time and effort I am not sure that I can understand the commands you gave me but they worked and eliminated the Google-earth directory...
NEVER again install this crap again...
under linux...
I will open it only under windows although I hate the restart and logon...

---

