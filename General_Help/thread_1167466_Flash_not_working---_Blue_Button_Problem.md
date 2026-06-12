---
title: "Flash not working--- Blue Button Problem"
date: 2009-05-22
forum: General Help
---

### Post by lazukars on 2009-05-22
I recently upgraded to Jaunty and now flash is not working properly in Firefox.  When you visit a website, a circular blue button appears in place of the flash content.  The only way you can get the flash to play is by clicking on the blue button.  

I have unistalled and reinstalled flash and am still having problems.  Please help.

Ryan

---

### Post by Ahadiel on 2009-05-22
Do you have any Firefox extensions enabled?

---

### Post by raymondh on 2009-05-22
Would you like to give this a try?

1) Uninstall/purge Flash from your system
2) With Firefox, visit a website that requires flash 
3) You will be prompted by firefox to install missing plugins
    and be given 3 choices (swfdec / adobe / gnash)
4) install the official adobe version (your password will be required)
5) click finish
6) check about:config to verify that you have flash
5) Reboot firefox and have a go

Another option is to terminal and install

```
sudo apt-get install flashplugin-installer
```

BTW, if you decide to install thru synaptic or the terminal, make sure multiverse repos ( 2 of them) are enabled in your sources. System > admin > software sources > third party

I hope this helps you.  It worked for me.

Good luck and regards,

---

### Post by lazukars on 2009-05-22
raymondhenson

I have tried purging and reinstalling flash and then tried:
sudo apt-get install flashplugin-installer

Both of those, unfortunatly did not solve the problem.



Ahadiel

I am not sure what you mean by this:
"Do you have any Firefox extensions enabled?"

---

