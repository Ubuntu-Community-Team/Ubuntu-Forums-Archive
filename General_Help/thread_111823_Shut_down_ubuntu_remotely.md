---
title: "Shut down ubuntu remotely"
date: 2006-01-03
forum: General Help
---

### Post by PryGuy on 2006-01-03
Hello everyone!
Well, this is my first post in the New Year! And I wish you all be healthy, wealthy and wise, and stay with Ubuntu in the New Year of course!:D

Now, the question: I want to install Ubuntu on my server (it's currently running Windows 2003 Server). I turn it on remotely using WOL and shut it down using Remote Desktop. The problem is that I have a few machines that I just can't switch to Ubuntu.:( Is there a possibility to shut down the Ubuntu machine from Windows? It'd be great if I could do it without installing additional software such as VNC client or something. Please list all the possibilities that you know... Thank you!:D

---

### Post by chocolatetoothpaste on 2006-01-03
The only thing I could think of is to download a program called PuTTY and install it on any windows machine, then you can run ```
shutdown now
``` or maybe ```
shutdown -now
``` from the command prompt.  PuTTY is free, and not too hard to configure as far as I know.  I don't think you have to do anything on the linux side, but I have been wrong more than once.  Maybe just allow remote logins, not sure.  Hope this helps

---

### Post by PryGuy on 2006-01-03
Thank you! But I know PuTTY already, and, well, I'm not sure my dad will be able to use it for instance. Ideally I'd love to use something like the native windows program called "shutdown". The best way would be to be able to make a CMD file that would do a remote shutdown for my server.

---

### Post by gibbylinks on 2006-01-03
Hi,

 Half an answer sorry.... I'm not at home so can't tell you the name of the program I'm using, it's not putty (no flippin help there !!), I think it's called WinSCP or something, but anyway. 

What I did is wrote a script using a text editor (I'm assuming putty can use scripts) and then placed a shortcut on my desktop configured to run the script. I have two icons, one for shutdown & one for reboot.

I'm sure your Dad is technically minded enough to double click an icon !!!

So I access my Linux PC using VNC from my WXP machine and use the icons to shutdown/reboot when I need to.

Hope this helps

Paul

---

### Post by PryGuy on 2006-01-03
[QUOTE=gibbylinks]I'm sure your Dad is technically minded enough to double click an icon !!!l[/QUOTE]You bet! LOL :D
Well, as for PuTTY, it'd be great if one could shutdown the machine using script without any interactivity, except for the double clicking an icon of course;). It'd be great if you could remember the name of the program you use for the remote shutdown. Thank you!

---

### Post by PryGuy on 2006-01-03
Anybody, pleeease...:)

---

### Post by chocolatetoothpaste on 2006-01-03
Sorry, I don't know enough about PuTTY to write scripts or anything, and I don't use it anymore, so I wish I could be more help!  Good luck!  I know you have probably tried this, but if not, google it.

---

### Post by sargek on 2006-01-04
You could install Webmin on the box and access it that way - webmin allows remote shutdowns. Not sure how secure this is - I believe you would have to have port 443 open (https), but not sure because I've only shut machines on my local lan down with webmin.

---

### Post by PryGuy on 2006-01-04
That's a great idea, thanks! I think one shouldn't care about security much if's allowed in my LAN only.

---

### Post by njparton on 2007-11-03
> **sargek said:**
> You could install Webmin on the box and access it that way - webmin allows remote shutdowns. Not sure how secure this is - I believe you would have to have port 443 open (https), but not sure because I've only shut machines on my local lan down with webmin.

I've just installed webmin on my headless ubuntu NAS, but I can't seem to see how to shut it down from within a browser in windows. I've been through all the default webmin menu options.

Any pointers?

Thanks

---

### Post by ruibernardo on 2007-11-03
> **njparton said:**
> I've just installed webmin on my headless ubuntu NAS, but I can't seem to see how to shut it down from within a browser in windows. I've been through all the default webmin menu options.

Any pointers?

Thanks

Go to the webmin menu in System > Bootup and Shutdown. "Reboot" and "Shutdown" buttons are on the end of that page.

---

### Post by njparton on 2007-11-04
Aha! Thanks - I'd never made it to the end of that long page!

---

