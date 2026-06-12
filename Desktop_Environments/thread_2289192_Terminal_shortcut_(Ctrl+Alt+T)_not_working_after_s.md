---
title: "Terminal shortcut (Ctrl+Alt+T) not working after shifting to metacity"
date: 2015-08-02
forum: Desktop Environments
---

### Post by Pablo_San_Martn on 2015-08-02
So in order to try some new window themes, I decided to switch from openbox to metacity using Lubuntu 14.04.

After switching, however, I noticed that I can no longer quicklaunch a terminal window with Ctrl+Alt+T. I've tried a couple of methods involving gconf and dconf but apparently the existing tutorials are too old or are meant for other linux distributions such as Gnome. 

Also, I've noticed Lubuntu doesn't come with the Keyboard Shortcuts GUI on the main menu. That's a shame but probably wouldn't solve my problem as it would be set to edit the openbox shortcuts file.

---

### Post by TheFu on 2015-08-02
[https://help.ubuntu.com/community/Metacity](https://help.ubuntu.com/community/Metacity) - take it you already saw that and it didn't work?

---

### Post by Pablo_San_Martn on 2015-08-02
Yes, TheFu, thanks, I've already tried that.

The thing is that the metacity entry does not appear in the Configuration Editor as it appears there. It only appears *after *I create the specific entries for global_keybindings and keybinding_commands, and then only the two entries I've created and the value for Key Owner in both of them is 'None'. Maybe this is because, as I've read elsewhere, metacity settings migrated to dconf?

---

### Post by TheFu on 2015-08-02
Figured you had.  I'm not finding anything more. Don't use metacity myself, but my openbox.rc file has been extensively modified since I don't have any panels/menus. Miss the days of fvwmrc ... but not the huge borders. ;)

---

### Post by vasa1 on 2015-08-02
> **TheFu said:**
> ..., but my openbox.rc file ...
What's openbox.rc?

---

### Post by TheFu on 2015-08-02
openbox has a file that controls all sorts of things - keyboard shortcuts, for example. lxde-rc.xml or lubuntu-rc.xml are a common names for it, but I think any .xml will work.

The bad thing is it is xml - really wish programmers would re-re-read the Unix Programmers Style Guide and stay with text files that humans can trivially read and modify.  There shouldn't be any need for anything other than an editor to control system settings.

IMHO.

---

### Post by vasa1 on 2015-08-02
> **Pablo_San_Martn said:**
> So in order to try some new window themes, I decided to switch from openbox to metacity using Lubuntu 14.04.
...
Also, I've noticed Lubuntu doesn't come with the Keyboard Shortcuts GUI on the main menu. ...
If you prefer metacity over openbox, why not switch to MATE? Doesn't 15.04 MATE come with metacity?

---

### Post by TheFu on 2015-08-02
I tried to run mutter alone today, but couldn't get it to --replace openbox  - kept getting kicked out to a login and mutter wasn't an option on the lightdm screen.  I run a plain openbox setup.

---

### Post by SantaFe on 2015-08-02
> **vasa1 said:**
> If you prefer metacity over openbox, why not switch to MATE? Doesn't 15.04 MATE come with metacity?

Sort of, it's version is called Marco.  See [http://manpages.ubuntu.com/manpages/utopic/man1/marco.1.html](http://manpages.ubuntu.com/manpages/utopic/man1/marco.1.html)

It does use Metacity themes though.   I think it's a fork of Metacity.

---

### Post by vasa1 on 2015-08-03
I saw this: [http://news.softpedia.com/news/Ubuntu-MATE-Now-Has-Supports-Marco-Compiz-Mutter-and-Metacity-481615.shtml](http://news.softpedia.com/news/Ubuntu-MATE-Now-Has-Supports-Marco-Compiz-Mutter-and-Metacity-481615.shtml)

So it seems that Marco *and* Metacity are supported.

---

### Post by Pablo_San_Martn on 2015-08-03
> **vasa1 said:**
> If you prefer metacity over openbox, why not switch to MATE? Doesn't 15.04 MATE come with metacity?

Thanks for the advice, I didn't know about MATE. I'll take a look.

But it's not that I prefer metacity over openbox - I love LXDE and Openbox, especially with Compton it works very well for me. I just wanted to try some rounded corner themes for a while, and as metacity comes already installed in Lubuntu (or it said it was already installed when I tried to install it) I thought I would give it a try. 

And it's only this tiny problem of not being able to launch a Terminal window with a shortcut that I needed help with.

---

### Post by vasa1 on 2015-08-03
> **Pablo_San_Martn said:**
> ... I just wanted to try some rounded corner themes for a while, and as metacity comes already installed in Lubuntu (or it said it was already installed when I tried to install it) I thought I would give it a try. 
...
Yes, from hanging out in the Openbox mailing list I got the impression that the Openbox devs won't *ever* do rounded corners. Fluxbox apparently does.

Re. metacity, it's not part of Lubuntu at least in 14.04. What's default in Lubuntu 14.04 is listed here:
[http://cdimage.ubuntu.com/lubuntu/releases/trusty/release/lubuntu-14.04-desktop-amd64.manifest](http://cdimage.ubuntu.com/lubuntu/releases/trusty/release/lubuntu-14.04-desktop-amd64.manifest)

---

### Post by Pablo_San_Martn on 2015-08-04
> **vasa1 said:**
> Yes, from hanging out in the Openbox mailing list I got the impression that the Openbox devs won't *ever* do rounded corners. Fluxbox apparently does.

Yes, I had figured out thus far. I'm back to Openbox now after just a couple of days. It's more costumisable and nicer in the windows cycling and the desktop changing dialogues. I'm mixing the Lubuntu, Numix and Radiance themes and something interesting is coming up. 

> **vasa1 said:**
> Re. metacity, it's not part of Lubuntu at least in 14.04. What's default in Lubuntu 14.04 is listed here:
[http://cdimage.ubuntu.com/lubuntu/releases/trusty/release/lubuntu-14.04-desktop-amd64.manifest](http://cdimage.ubuntu.com/lubuntu/releases/trusty/release/lubuntu-14.04-desktop-amd64.manifest)

Thanks for the info. Is there any command I can use to find out when I installed the metacity packages?

---

### Post by TheFu on 2015-08-04
If you like lite and pretty - fvwm-crystal.
[https://help.ubuntu.com/community/FVWM-Crystal](https://help.ubuntu.com/community/FVWM-Crystal)

---

### Post by vasa1 on 2015-08-04
> **Pablo_San_Martn said:**
> ... Is there any command I can use to find out when I installed the metacity packages?

If you haven't run *sudo apt-get clean* after installing metacity, you may want to look through */var/cache/apt/archives*.

Otherwise, you could look through *history.log* in */var/log/apt*. Because of *logrotate*, that information may be moved to compressed files (history.log.gz) and even older data may be lost.

```
cd /var/log/apt && cat history.log > ~/Desktop/allhistory.log && zcat history.log*gz >> ~/Desktop/allhistory.log
``` will create the text file "allhistory.log" on your desktop which you can browse.

---

### Post by TheFu on 2015-08-04
Very nice cmd.  Think that I'll be adding that to my pre-backup jobs.  Having that data available during a restore could be very helpful.  I'm already doing a **dpkg --get-selections** and saving that, but ... for this data at 120Kb (current size) is trivial.  No - I don't backup /var/apt.

---

### Post by Pablo_San_Martn on 2015-08-04
> **vasa1 said:**
> Otherwise, you could look through *history.log* in */var/log/apt*. Because of *logrotate*, that information may be moved to compressed files (history.log.gz) and even older data may be lost.

```
cd /var/log/apt && cat history.log > ~/Desktop/allhistory.log && zcat history.log*gz >> ~/Desktop/allhistory.log
``` will create the text file "allhistory.log" on your desktop which you can browse.

That was superb!

Apparently metacity was installed when I executed the commands:
```

aptdaemon role='role-install-packages' sender=':1.116'

aptdaemon role='role-commit-packages' sender=':1.45'
```

I must have done it unwittingly, as I'v got no idea what that does.

---

### Post by vasa1 on 2015-08-04
> **Pablo_San_Martn said:**
> That was superb!

Apparently metacity was installed when I executed the commands:
```

aptdaemon role='role-install-packages' sender=':1.116'

aptdaemon role='role-commit-packages' sender=':1.45'
```

I must have done it unwittingly, as I'v got no idea what that does.
This *aptdaemon* stuff seems to be the way software is installed when you use a software manager such as USC and possibly synaptic. I use plain *apt-get* and don't have any such entries in my logs.

---

### Post by vasa1 on 2015-08-04
> **TheFu said:**
> Very nice cmd.  Think that I'll be adding that to my pre-backup jobs.  Having that data available during a restore could be very helpful.  I'm already doing a **dpkg --get-selections** and saving that, but ... for this data at 120Kb (current size) is trivial.  No - I don't backup /var/apt.
The main drawback is that logrotate will get rid of older logs. I guess one could edit the relevant logrotate file to ensure that more logs be retained. But I haven't done that although I remember asking about it here or @ Ask Ubuntu: [http://askubuntu.com/questions/421063/how-can-i-know-how-many-archived-logs-are-saved](http://askubuntu.com/questions/421063/how-can-i-know-how-many-archived-logs-are-saved)

I think I didn't go ahead because it involved editing system files in */etc/logrotate.d/apt* and then I'd have to somehow ensure that I restore my chosen values in case of a system update.

I think it makes more sense to run *dpkg --get-selections* periodically as you've suggested.

---

### Post by TheFu on 2015-08-04
> **vasa1 said:**
> The main drawback is that logrotate will get rid of older logs. I guess one could edit the relevant logrotate file to ensure that more logs be retained. But I haven't done that although I remember asking about it here or @ Ask Ubuntu: [http://askubuntu.com/questions/421063/how-can-i-know-how-many-archived-logs-are-saved](http://askubuntu.com/questions/421063/how-can-i-know-how-many-archived-logs-are-saved)

I think I didn't go ahead because it involved editing system files in */etc/logrotate.d/apt* and then I'd have to somehow ensure that I restore my chosen values in case of a system update.

I think it makes more sense to run *dpkg --get-selections* periodically as you've suggested.

Logrotate is easy.  Looking at the /etc/logrotate.d/dpkg file ... 
It rotates monthly and keeps 12 of them.  Want more?  Change the 12 to 48 - that will keep 48 months.  Be certain to put this in your devops tools, so it doesn't get forgotten at a fresh rebuild.  Those files are tiny (relatively - most are LT 10Kb) on my systems - I don't see any reason NOT to retain 48 months.

Of course, if you make changes, be certain to restart the service.

---

### Post by vasa1 on 2015-08-04
> **TheFu said:**
> ... I don't see any reason NOT to retain 48 months.
...
Yes, but the file is a system file. I'll need to keep checking to know if it ever changes as a consequence of a system update.

---

### Post by TheFu on 2015-08-04
> **vasa1 said:**
> Yes, but the file is a system file. I'll need to keep checking to know if it ever changes as a consequence of a system update.

Config files shouldn't be touched without warning - there should be a merge/diff option during patching.  

A DevOps tool to maintain system configs is handy, if you have enough to make it worth the effort.

---

### Post by vasa1 on 2015-08-04
> **vasa1 said:**
> ...
```
cd /var/log/apt && cat history.log > ~/Desktop/allhistory.log && zcat history.log*gz >> ~/Desktop/allhistory.log
``` will create the text file "allhistory.log" on your desktop which you can browse.

[s]That a text file will be created is **WRONG**. The filetype is "data" even if I rename *allhistory.log* to *allhistory.txt* :( [/s]

And different text editors handle the file differently. Both Mousepad and Leafpad show me 717 lines whereas Medit and nano show me 1329 lines. Geany says that > The file "/home/vasa1/Desktop/allhistory.txt" does not look like a text file or the file encoding is not supported.and shows me nothing.

Edit: 
I went back and ran* zcat* on each compressed file. Of the nine, eight showed up as "ASCII text, with very long lines". One was  "data". I wonder why.

Edit: I opened allhistory.log in LibreOffice Writer and found that the part corresponding to the "data" file had unusual characters in it. I guess something went wrong when the compressed file was created.

---

### Post by Pablo_San_Martn on 2015-08-06
> **vasa1 said:**
> This *aptdaemon* stuff seems to be the way software is installed when you use a software manager such as USC and possibly synaptic. I use plain *apt-get* and don't have any such entries in my logs.

Yes, you're right - I use both Lubuntu Software Centre and Software Updater. 

Is ```
sudo apt-get upgrade
``` enough to get the system updated?

---

### Post by Pablo_San_Martn on 2015-08-06
> **TheFu said:**
> If you like lite and pretty - fvwm-crystal.
[https://help.ubuntu.com/community/FVWM-Crystal](https://help.ubuntu.com/community/FVWM-Crystal)

Thanks for the heads-up, handn't seen this before :D

---

### Post by TheFu on 2015-08-06
Maintaining an Ubuntu Desktop: [http://blog.jdpfu.com/linsysmaint](http://blog.jdpfu.com/linsysmaint)
That is all you need.

---

### Post by vasa1 on 2015-08-06
> **Pablo_San_Martn said:**
> ...
Is ```
sudo apt-get upgrade
``` enough to get the system updated?I use *sudo apt-get dist-upgrade*. I understand that some updates aren't offered via *sudo apt-get upgrade*.

---

### Post by Pablo_San_Martn on 2015-08-06
Thanks again to both of you. This has been really helpful.

---

