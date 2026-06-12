---
title: "I need to change Kmail's default browser in Gnome"
date: 2009-01-24
forum: General Help
---

### Post by ooolongT on 2009-01-24
I am running Intrepid with Gnome.  However, I like Kmail.  So, what I need to do is keep my Gnome deskop and Kmail, but change the browser that it opens when I click on a link from opera to epiphany.  


Because I am running Gnome, I do not have the KDE Contol Center installed, and I would prefer to change the appropriate config file to avoid installing any more software.

Thanks!

---

### Post by dcstar on 2009-01-24
> **ooolongT said:**
> I am running Intrepid with Gnome.  However, I like Kmail.  So, what I need to do is keep my Gnome deskop and Kmail, but change the browser that it opens when I click on a link from opera to epiphany.  
........

System-Preferences-Preferred Applications

---

### Post by ooolongT on 2009-01-24
Thanks David, I tried that, but it does not change it for Kmail for some reason.

---

### Post by ooolongT on 2009-01-25
Can I get a bump bump!?!?:D

---

### Post by simon_ives on 2009-01-29
I wish I could figure this out too.  Currently kmail is opening Bluefish on my system.  I can't figure out how to change this

---

### Post by ooolongT on 2009-01-29
I hear ya simon!  So I looked in /.kde/share/config, and looked at ALL of those files and I could not find it anywhere.  Then I ran find in a terminal and found a grip of possibilities.  Among them:

/usr/share/kde4/config.kcfg/kmail.kcfg
/usr/share/kde4/apps/kmail/kmail_part.rc
/usr/share/kde4/services/kmail_config_misc.desktop
/usr/share/kde4/services/kontact/kmailplugin.desktop

I will take a look at some of these and see if what I can learn.  Let me know if you figure anything out.

---

### Post by ooolongT on 2009-02-02
Simon, I hope youre still with me on this, because I think IL am narrowing it down.  

You should be able to find the "kmailrc" (config) file here:

~/.kde/share/config/kmailrc 

That file has a ton of things you can set in it, but I do not see a line where you can change the browser.  But I think we are at least in the right directory.  I will let you know if I find it.

---

### Post by kyuso on 2009-02-09
If you are using gnome,

run konqueror, Settings->Configure konqueror, click File Associations, click text, html, click browser of your choice and move up to the top of the list.

I found this solution somewhere on the web when I had the same problem.

---

### Post by ooolongT on 2009-02-11
Kyuso, Thanks for the tip.  I was hoping not to have to install any new software, but right now, its not looking like I have much of a choice since no one seems to know where the right config file is.  

I am going ot leave this posted to see if anyone else has any ideas.

---

### Post by earlra on 2009-05-02
I was having the same issue, having recently switched to Gnome when I upgraded to 9.04 (to avoid KDE 4).  I love Kmail and made it the default instead of Evolution, but had the same problem.  I applied kyuso's tip and it worked just fine for me.

Regarding your comment about installing new software, were you referring to installing Konqueror?  You won't have to install it; it looks to me like when you install Kmail it auto-installs some KDE apps, like Konqueror and Kwallet, that it normally relies upon.

Thanks kyuso, this solved an annoyance for me!

---

### Post by costamatrix on 2009-05-05
i have the same problem....

i tryied to use konqueror to change de defaul browser, but it crashes saying:

konqueror(16130) KonqViewManager::setCurrentProfile: "webbrowsing" localPath= "/home/rodrigo/.kde/share/apps/konqueror/profiles/webbrowsing"
konqueror(16130) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: khtml_general.desktop not found"
konqueror(16130) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kcmkonqyperformance.desktop not found"
konqueror(16130) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: bookmarks.desktop not found"
konqueror(16130) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: filebehavior.desktop not found"
KCrash: Application 'konqueror' crashing...
sock_file=/home/rodrigo/.kde/socket-rodnote/kdeinit4__0


remember, i am using kontact on my gnome.

---

### Post by mulvila on 2009-05-11
> **kyuso said:**
> If you are using gnome,

run konqueror, Settings->Configure konqueror, click File Associations, click text, html, click browser of your choice and move up to the top of the list.

I found this solution somewhere on the web when I had the same problem.

Hi, I had to install konqueror to to this, but works now well. Thanks a lot for the hint.

---

### Post by ooolongT on 2009-05-11
As far as I can tell this is the only way to change this setting.  You must install Konquorer.  I do not believe there is a way to make this change without it, even though I was trying to avoid installing anything else.  Thanks everyone, I am going to mark this solved.

---

