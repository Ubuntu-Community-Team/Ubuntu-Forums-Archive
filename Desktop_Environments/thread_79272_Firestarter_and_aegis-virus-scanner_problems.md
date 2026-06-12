---
title: "Firestarter and aegis-virus-scanner problems"
date: 2005-10-19
forum: Desktop Environments
---

### Post by DeathOnJuice on 2005-10-19
I'm having a few problems with firestarter and aegis-virus-scanner, which I recently downloaded. After I got them both off of Synaptic, I restarted. I noticed firestarter didn't start automatically, so I opened a terminal and did sudo firestarter. I configured it, and the status windows popped up. However, whenever I close the status window, it gets rid of the icon in the taskbar as well (closes the program)! Do I have to have that status window up all the time to have a firewall running?

Also, when I run sudo aegis-virus-scanner, a message pops up that says a new version of File::Scan is available. I click yes when it asks if I want to get it, then it asks for my root password. Then, it says something about perl and saying yes to configure or no to auto-configure. I typed no because I knew nothing about perl, then it outputted some text. It seemed to be stuck on getting some file, so I pressed control-C, restarted aegis, and tried again. This time I didn't get a yes or no option about the perl thing, and it went straight to the files. It seemed to work until the very end, when I managed to see something about "make returning bad status" before the window closed. I tried again with the same results. Can anyone help me out?

Thanks in advance!

---

### Post by Chris Cromer on 2005-10-19
To get the icon to stay in firestarter, go into Edit > Preferences

Now select both the "Enable tray icon" and "Minimize to tray on close" check boxes. Then hit accept.

Now when you close the status window it will shrink down to the icon.

And are you also wanting it to automatically startup when you login? If so follow the instructions here: [http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

---

### Post by DeathOnJuice on 2005-10-20
OK, thanks for that help. It seems to be working (I haven't restarted to see if it starts at startup yet). However, I still need help with the Aegis problem.

---

### Post by Efwis on 2005-10-20
[QUOTE=Chris Cromer]

And are you also wanting it to automatically startup when you login? If so follow the instructions here: [http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)[/QUOTE]
You should follow the debian setup.

```

username ALL= NOPASSWD: /usr/sbin/firestarter
```

---

### Post by flyingbrass on 2005-10-21
[QUOTE=Efwis]You should follow the debian setup.

```

username ALL= NOPASSWD: /usr/sbin/firestarter
```[/QUOTE]

Be sure to make that the last line in your sudoers file.  It must be after the %admin entry.

---

### Post by DeathOnJuice on 2005-10-21
OK, I got that working, but I still don't get the Aegis thing,,,

---

### Post by DeathOnJuice on 2005-10-23
OK, I managed to get a screenshot of the error. Here are the last few lines:

Checking if your kit is complete...
Looks good
Writing Makefile for File::Scan
         --- NOT OK
Running make test
         Can't test without successful make
Running make install
         make had returned bad status, install seems impossible

NOW can anyone PLEASE help me?!?!? I need those virus definitions!!!

---

### Post by nix4me on 2005-10-23
You need to install the build-essential package.

nix4me

---

### Post by DeathOnJuice on 2005-10-25
Thanks, but that doesn't seem to work. I installed it, then tried to update again, and it failed.

THIS IS REALLY GETTING ****ING ANNOYING!!!

---

### Post by Efwis on 2005-10-25
[QUOTE=DeathOnJuice]Thanks, but that doesn't seem to work. I installed it, then tried to update again, and it failed.

THIS IS REALLY GETTING ****ING ANNOYING!!![/QUOTE]
for some reason the automatic updater isn't working so you need to do the following.
also you do not need build essentials as I don't have it installed and it worked fine.

download the tar.gz file [Here](http://search.cpan.org/CPAN/authors/id/H/HD/HDIAS/File-Scan-1.43.tar.gz)
extract it from the archive. I downloaded mine to my desktop and did it all there.

next open a terminal and type the following
```

cd /home/xxx/Desktop/scan-file-1.43
```
xxx =  the name you set up when you installed your distro.

now that you are in that file do the following to make and install the file:
```

sudo perl Make.PL
sudo make
sudo make test
sudo make install
```

Now I used my root terminal so I don't know if you will get asked for password after each sudo command or not. If I'm not mistaken you do,but I could be wrong.

Thats it you just installed th update.

---

### Post by Justin Morgan on 2005-11-16
Hi, When i tried to do what was mentioned above to update the Aegis Virus scanner it said in the terminal window that "make" is not a valid command, am I doing something wrong? Thanks.

---

### Post by bryan986 on 2005-11-17
[QUOTE=Justin Morgan]Hi, When i tried to do what was mentioned above to update the Aegis Virus scanner it said in the terminal window that "make" is not a valid command, am I doing something wrong? Thanks.[/QUOTE]

You need to install build-essential as listed before

---

### Post by Efwis on 2005-11-17
[QUOTE=Efwis]for some reason the automatic updater isn't working so you need to do the following.
also you do not need build essentials as I don't have it installed and it worked fine.

download the tar.gz file [Here](http://search.cpan.org/CPAN/authors/id/H/HD/HDIAS/File-Scan-1.43.tar.gz)
extract it from the archive. I downloaded mine to my desktop and did it all there.

next open a terminal and type the following
```

cd /home/xxx/Desktop/scan-file-1.43
```
xxx =  the name you set up when you installed your distro.

now that you are in that file do the following to make and install the file:
```

sudo perl Make.PL
sudo make
sudo make test
sudo make install
```

Now I used my root terminal so I don't know if you will get asked for password after each sudo command or not. If I'm not mistaken you do,but I could be wrong.

Thats it you just installed th update.[/QUOTE]

This should help you out. Make sure you do everything as I stated above.

---

### Post by mcduck on 2005-11-17
[QUOTE=DeathOnJuice]I'm having a few problems with firestarter and aegis-virus-scanner, which I recently downloaded. After I got them both off of Synaptic, I restarted. I noticed firestarter didn't start automatically, so I opened a terminal and did sudo firestarter. I configured it, and the status windows popped up. However, whenever I close the status window, it gets rid of the icon in the taskbar as well (closes the program)! Do I have to have that status window up all the time to have a firewall running?
[/QUOTE]
I just tought that it might be worth telling you that you don't need to have Firestarter open to have a firewall. Firestarter is just a GUI tool for configuring and monitoring your built-in firewall called iptables. Firewall is started on boot, and opening or closing the Firestarter window doesn't start or stop the firewall.

---

### Post by Icefox on 2005-11-18
1)Open Synaptic->Search->build-essential->install
2)sudo perl Makefile.PL
  sudo make
  sudo make test
  sudo make install

Done...your Aegis-Virus-Scanner is up to date

---

