---
title: "adept auto updater"
date: 2006-06-14
forum: Desktop Environments
---

### Post by kb3hkg on 2006-06-14
After upgrading to Dapper Adept had this nice auto updater that I accidently made go away. I have looked around to try to find a way to bring it back but have been unsuccesful. Can anyone tell me how to do this?

---

### Post by Jucato on 2006-06-14
You're probably talking about Adept Notifier in the system tray icon that informs you if there are upgradeable packages. It really "goes away" when there are no more packages available for upgrade. It reappears whenever there are. It usually checks for upgrades whenever you log in to Kubuntu.

Don't worry, it's still running in the background. To make sure it is still there, press Ctrl+Esc (launches Processes Table), and look for adept_notifier. If it's still there, you have nothing to worry about.

---

### Post by kb3hkg on 2006-06-14
that's the thing, it's not there anymore. How do I get it to be running again automatically? It no longer runs on its own.

---

### Post by Jucato on 2006-06-14
To make it run automatically when you log in to Kubuntu:
Check if there's a file named *adept_notifier_auto.desktop* in the /usr/share/autostart/ directory. If it isn't there, make one:
1. Open up Kate as root. Press Alt+F2 and enter the following command:
```
kdesu kate
```
2. Paste in the following contents:
> 
[Desktop Entry]
Encoding=UTF-8
Exec=adept_notifier
Name=Adept Notifier
Name[da]=Adept underretninger
Name[el]=•¹´¿À¿¯·Ã· µ½·¼µÁÎÃµÉ½ Ä¿Å Adept
Name[es]=Notificador Adept
Name[fr]=Notificateur Adept
Name[it]=Notifica automatica Adept
Name[ka]=Adept èÔÛâçÝÑØÜÔÑÔÚØ
Name[lt]=Adept informuoklis
Name[pt]=Notificador do Adept
Name[sk]=Adept upozornenie
Name[sv]=Adept uppdatering
Name[xx]=xxAdept Notifierxx
X-KDE-autostart-after=panel
Type=Service
X-KDE-autostart-condition=adept_notifierrc:General:Autostart:true
OnlyShowIn=KDE;

3. Save the file as *adept_notifier_auto.desktop* and save it in the /usr/share/autostart/ directory.

That should do it.
If you need to manually launch Adept Notifier, press Alt+F2 and enter *adept_notifier*.

---

### Post by kb3hkg on 2006-06-15
already looked pretty much like that. Only differences were in the names area, any other ideas?

---

### Post by kb3hkg on 2006-06-17
I got the notifier up and running again, but now it doesn't disappear from the system tray. How do I fix this?

---

### Post by pizeta on 2006-06-19
i solved in this way:
[http://ubuntuforums.org/showthread.php?p=1156648](http://ubuntuforums.org/showthread.php?p=1156648)

if that's not your problem look at the timestamp of these two file
/var/cache/apt/pkglist.bin
/var/lib/dpkg/status
if one of these files have the timestamp in the future your adept_notifier thinks that there are some upgradable packages

Last chance close adpet_notifier, run it again from your console and paste the output

---

### Post by kb3hkg on 2006-06-19
well the first mentioned file doesn't exist, and the second seems fine.

However, sources.list isn't user readable, fixing this has worked. Thank you very much.

---

### Post by astromech on 2007-09-02
> **Jucato said:**
> To make it run automatically when you log in to Kubuntu:
Check if there's a file named *adept_notifier_auto.desktop* in the /usr/share/autostart/ directory. If it isn't there, make one:
1. Open up Kate as root. Press Alt+F2 and enter the following command:
```
kdesu kate
```
2. Paste in the following contents:

3. Save the file as *adept_notifier_auto.desktop* and save it in the /usr/share/autostart/ directory.

That should do it.
If you need to manually launch Adept Notifier, press Alt+F2 and enter *adept_notifier*.


Everything was in the file as you posted it i manually launched adept as you suggested and it told me i had disabled the notifier the last time i used it  OOOPS!!!:lolflag:

---

### Post by astromech on 2007-09-02
> **Jucato said:**
> To make it run automatically when you log in to Kubuntu:
Check if there's a file named *adept_notifier_auto.desktop* in the /usr/share/autostart/ directory. If it isn't there, make one:
1. Open up Kate as root. Press Alt+F2 and enter the following command:
```
kdesu kate
```
2. Paste in the following contents:

3. Save the file as *adept_notifier_auto.desktop* and save it in the /usr/share/autostart/ directory.

That should do it.
If you need to manually launch Adept Notifier, press Alt+F2 and enter *adept_notifier*.


Everything was in the file as you posted it i manually launched adept as you suggested and it told me i had disabled the notifier the last time i used it  OOOPS!!!:confused::lolflag:

---

### Post by mastergunner on 2007-09-08
I have done all of this and I can not get adept notifier to run. If I rum it in Konsole nothing happens. It looks like this:

brad@brad-laptop:~$ adept_notifier
brad@brad-laptop:~$
 
What gives?

---

