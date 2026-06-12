---
title: "firewall monitor applet"
date: 2006-11-21
forum: Desktop Environments
---

### Post by RikoW on 2006-11-21
Hi all,

I'm looking for a simple application which monitors the firewall logs to report events blocked etc. The application should run in the notification area so that I see when something happens.

When running firestarter with the gui, it does what I want (like changing the icon form blue to red in case of an event), but I don't want to run firestarter all the time with admin rights just to keep an eye on things.

Anybody come across a graphical monitor for the panel?

Thanks,

          Riko

---

### Post by Jimmey on 2006-11-21
Ehrm, Firestarter's all good.

I think there's a HOWTO somewhere that explains how you can have firestarter run at boot without making you enter a password. Let me find it...

I've been quite lazy and not really checked over this link, but try [here]("http://ubuntuforums.org/archive/index.php/t-33615.html") anyway. Hope this help :-)

---

### Post by RikoW on 2006-11-21
> **Jimmey said:**
> Ehrm, Firestarter's all good.


I know that! :)

But I'm looking for something which runs just in the user space without admin rights. 
Maybe, the applet could even be a  bit more talkative at the tooltip about the events blocked by the firewall than firestarter is without opening the gui.

Cheers,

            Riko

---

### Post by Jimmey on 2006-11-21
I don't know if there's anything else that does that. Maybe try "apt-cache search firewall" to see if there are any packages that are matching your requirements. If there are, "sudo apt-get install package-name".

There's a number of network monitors available (maybe try conky?) but none that I can recall monitor blocked connection attempts.

---

