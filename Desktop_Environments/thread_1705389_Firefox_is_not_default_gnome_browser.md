---
title: "Firefox is not default gnome browser"
date: 2011-03-12
forum: Desktop Environments
---

### Post by vedovatti on 2011-03-12
Hi there,
I have a problem setting Firefox as default browser for links on gnome programs. I installed Chrome and (somehow) it set up in gnome as default.

I tried everything and still no result. Seems to be problem with the gnome default browser. So here is what I tried up to now.

Got Menu>Preferences>Preferred application - Set Firefox as default browser.
```
sudo update-alternatives --config x-www-browser
sudo update-alternatives --config gnome-www-browser
```
And set up as Firefox as default browser. (It calls my attention that it offer 3 options: 2 Chrome [auto and manual] and Firefox [manual] could it be the problem?

So basically when I click in any link in Evolution it start the link in Chrome. When I click on the link in Yelp, the same or in Tomboy, etc.

I tried to uninstall Chrome, but when I click on any link it says: /opt/google/chrome/google-chrome not found. So it means that I must have it install.

Any ideas about this? I have Ubuntu 10.04 and the lastest versions of both browsers

Thanks

---

### Post by kc1di on 2011-03-12
When you say Chrome are you talking about Chromium that you install from The Ubuntu Repository via synaptic or apt-get or one you downloaded from Chrome site and install manually?

That's important because they do not install the same.  and that may be the problem.  I have chromium installed here and can switch back and forth in System >Preferences> Preferred Application with no problem and evolution links go to which ever one I've set.  

So I don't think the problem is with gnome.

---

### Post by vedovatti on 2011-03-12
Hi thanks for the reply.
I am talking about Chrome, I download it from the website. 

I was thinking about Chromium but I dont want to have 3 browsers.

The problem is the Chrome.deb I download from Google website.

---

### Post by kc1di on 2011-03-12
unfortunately I think the chrome .deb though it will install correctly does not place all the files that chromium does in the same places. so gnome doesn't see the files it needs to make the change and the Chrome files over ride the gnome preferences I notice this also on a previous install.

I find that the Ubuntu team does a great job in keeping chromium up to date and thus see no reason to use Chrome. 

Just my thoughts .

---

### Post by Krytarik on 2011-03-12
@kc1di: Since the OP already removed Google Chrome, and it is still pulled as the default browser, your advice doesn't help at this moment.

@vedovatti: I just yet downloaded and checked the deb-file. Check in "/usr/share/gnome-control-center/default-apps" if the file "google-chrome.xml" is still there. If so, remove it. Also re-check the respective option in "Preferred Applications".

Also check the other file mentioned in "google-chrome.xml":
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE default-apps SYSTEM "gnome-da-list.dtd">
<!-- This file should be put in /usr/share/gnome-control-center/default-apps,
     or, if that directory does not exist, its web-browser tag patched into
     /usr/share/gnome-control-center/gnome-default-applications.xml -->
<default-apps>
  <web-browsers>
    <web-browser>
      <name>Google Chrome</name>
      <executable>/opt/google/chrome/google-chrome</executable>
      <command>/opt/google/chrome/google-chrome %s</command>
      <icon-name>google-chrome</icon-name>
      <run-in-terminal>false</run-in-terminal>
      <netscape-remote>true</netscape-remote>
      <tab-command>/opt/google/chrome/google-chrome %s</tab-command>
      <win-command>/opt/google/chrome/google-chrome --new-window %s</win-command>
    </web-browser>
  </web-browsers>
</default-apps>
```

---

### Post by vedovatti on 2011-03-12
Hi there,

Thank you for your answers. You are right about Chromium, I should have used since the beginning but unfortunately I didn't know it exist. I installed Chrome because I wanted to have 2 web-browser. A pity because I really use it seldom (maybe once a month).

I checked the file /usr/share/gnome-control-center/default-apps

there is nothing there about Chrome and checked again the default application menu, firefox still as default.

Still the same if I dont install back Chrome the links that I click dont work. It's so anoying!

Any more ideas. Thanks

---

### Post by Krytarik on 2011-03-12
In fact I have also Chromium installed as the second browser. And I use from time to time, more for test purposes, but only today I noticed how blazingly fast it starts up compared to Firefox, even Firefox 4 doesn't start up that fast! But the browsing speed is comparable to both Firefox versions.

Anyway, check this solution:
[http://ubuntuforums.org/showthread.php?p=9665492](http://ubuntuforums.org/showthread.php?p=9665492)

Of course you have to do it the other way around, I would change the setting with gconf-editor.

---

### Post by XsheepX on 2011-03-12
In Firefox, go to Edit>Preferences>Advanced tab, and check the box that says "Always check to see if Firefox is the default browser on startup."
Restart Firefox, and it will prompt you to set it as the default again.

---

### Post by vedovatti on 2011-03-13
Hi guys,

thanks again.

I tried both of the solutions. Unfortunately, it didn't work.

I have checked the gconf on the Desktop>gnome>usr handlers, all is set up for: "Firefox %s". I search in all the paterns in gconf and none of them mentions Chrome.

I check as well the Advanced tab of Firefox, it always check the default browser.

This is driving me crazy. You are right I like Chromium is faster than firefox but I like firefox because I have all the addons and really personalized since a couple of years, in some kind of way I feel more secure. Anyway that is another topic.

My problem still the same Chrome is default browser for all wwww-links and hyperlink in gnome for every program: Evolution, openoffice, tomboy, etc.

:(

---

### Post by Krytarik on 2011-03-13
> **vedovatti said:**
> You are right I like Chromium is faster than firefox but I like firefox because I have all the addons and really personalized since a couple of years, in some kind of way I feel more secure. Anyway that is another topic.

The same is true for me!

Did you also check "/usr/share/gnome-control-center/gnome-default-applications.xml", like I mentioned.

And as for the "update-alternatives" commands, apparently it won't affect the actual handling, at least at my system. It says Chromium is set to auto, but I didn't chose it, and links and html files are opened with Firefox.

**Addition:** Could you please also try choosing "Custom" in "Preferred Applications" and set the command to "firefox %s".

---

### Post by vedovatti on 2011-03-13
Hi,

Yes, I checked the file: /use/share ... .xml

No mention of Chrome.

I tried to set up: Custom web browser but when I type Firefox %s it just choose automatically the first option. I doesn't allow me to use the Firefox as custom because it changes.

On the other hand, when type:
```
sudo update-alternatives --config x-www-browser
```
I see all the alternative and Chrome is the only one that says auto mode, even if firefox is selected. I don't know what means that auto mode. Could it be the problem? Does anybody know how to change it?

Thanks

---

### Post by Krytarik on 2011-03-13
I believe the "auto" option simply causes to try the specified one, in this case Chrome, and if that doesn't work because the program isn't there or such, it should fallback to next one regarding the priority.

I thought you did remove it!? Remove it again, then select Firefox with this command.

After all, if that still doesn't work, you could do a *ugly* workaround by simply symlinking Firefox' executable to those stated for Chrome.

---

### Post by vedovatti on 2011-03-14
Hi

I had to reinstall Chrome again because if not the links always fails. 

I tried again to uninstall it, and still the same problem.

I will do the symlinking. It is a bit complicated because is exec and need a script (I think...) and as you say: is a bit ugly but anyway... a workaround. 

I cannot believed that I am the only one affected by this.

Thanks again

---

### Post by Krytarik on 2011-03-14
The commands for the symlink workaround would be like this:
```
sudo mkdir /opt/google
sudo mkdir /opt/google/chrome
sudo ln -s /usr/bin/firefox /opt/google/chrome/google-chrome
```Sorry, I don't have a better solution right now. But I'll take a further look into this later.

---

### Post by Krytarik on 2011-03-14
After taking one more look into the google-chrome package I got one idea:
- check the content of "~/.local/share/applications/mimeapps.list", you may post it
- if google-chrome is listed there, remove it and remove the would-be corresponding .desktop-file in "~/.local/share/applications" as well

---

### Post by vedovatti on 2011-03-15
Thank you very much for your help.

I can say that I solved it!

I don´t really know how. My solution was this: as I tried to uninstall everything that was useless in the computer, like kde programs, configuration not used anymore, old stuff, anyway I just erased all the programs that I am not using.

And magically it work know. So it was some package, or old configuration that was making trouble. I cannot really say what was the program but it is solved.

Krytarik thank you very much for your help! its the second time you help me with this :D

---

### Post by Krytarik on 2011-03-15
> **vedovatti said:**
> 
Krytarik thank you very much for your help! its the second time you help me with this :D
Ah, I see, that was also you! You're welcome!

---

### Post by rubic on 2011-10-02
From xfce (+xmonad), I solved this by entering on the command line:

[FONT="Courier New"]$ gnome-default-applications-properties[/FONT]

---

