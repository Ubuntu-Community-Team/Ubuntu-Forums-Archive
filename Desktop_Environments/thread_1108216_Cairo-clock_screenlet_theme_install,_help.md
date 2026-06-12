---
title: "Cairo-clock screenlet theme install, help"
date: 2009-03-27
forum: Desktop Environments
---

### Post by Cormerin on 2009-03-27
Hi, I've downloaded this 95788-Cockpit_0.9.tar cairo-clock theme from gnomelook.org 

How do I install it into the screenlet?

Thanks

---

### Post by Cormerin on 2009-03-27
Nevermind, I figured it out.

---

### Post by paxxus on 2010-11-10
> **Cormerin said:**
> Nevermind, I figured it out.
Thanks man, that was really helpful.

---

### Post by ben2talk on 2010-12-01
Lolz @Paxxus

Come on guys - don't say 'ok, I fixed it' because that helps nobody.

You should put HELP in here.

I have Cairo-clock, with themes in /usr/share/cairo-clock/themes but these aren't picked up by the screenlet. My search led me here first, and there isn't an answer - this is bad for Ubuntu users.

Now I'm not sure what folder the screenlets go to, but after installing them to the above folder, I opened nautilus (root - gksu nautilus) and browsed to /usr/share/cairo-clock/themes and copied the contents to desktop, changing properties to enable read-write for me. Then I used the screenlets manager, selected the clock, and then clicked 'install themes' from the left hand menu.

After restarting the clock, the themes are available.

---

### Post by Chazz44able on 2010-12-28
I have my clock folder in home/.config/cairo-dock/extra/cairo-clock and if you drop the clock themes into there, you can proceed to activate the clock in your dock by changing the theme(it'll appear there).

---

### Post by rs87424 on 2010-12-30
Hey guys,

I have had a few issues with this screenlet application and its really frustrating. I tried to install the flip theme for the clock screenlet and I have a similar problem.

So how would I drag and drop this extracted zip file into the share folder? 

Also, instead of opening my home folder from the main menu the screenlet application will pop up instead of the folder... I have to put nautilus into my terminal just to see my home folder...

I wonder if its related to the screenlet application?

Help would be much appreciated!

---

### Post by evoka0 on 2011-01-10
Probably this will help: the screenlets clock themes to be imported are supposed to be in a tar.bz2 file, with a theme.conf file inside, along with all the svg files.  Since the cockpit clock doesnt have a theme.conf file, I made mine with 2 lines 
 
```
[Theme]
name=Cockpit

```Then the theme is compressed into a tar.bz2 file, and imported as before. 

However I wanted my theme to be on my /home/  so I saved all the svg files and the theme.conf in ~/.screenlets/Clock/themes/Cockpit_Screenlet/

---

### Post by Zozz999 on 2011-01-21
First extract the themes from the tar.gz
Go to terminal and type: gksu nautilus
In the root folder, on the left side click: File System/usr/share/cairo-clock/themes
Once there just drag and drop your wanted themes into the themes folder
Done ;)

---

### Post by rs87424 on 2011-01-21
thanks I forgot I was supposed to do that. Now I just realized that the author of the article that I downloaded the tar.gz keeps removing the file. Now I am not sure I should download that one again. Has anyone else had a similar problem?

---

### Post by tnt533 on 2011-05-15
I just installed a cairo-clock theme downloaded from gnome-look by simply opening the Screenlets manager, selecting the clock screenlet in the list and then clicking on install new theme on the left. I browsed to where the tar file containing theme was located and clicked OK. BAM!

Restart the clock screenlet on your desktop then the theme will be in the list. Easy, peasy.

You can delete the tar file after install.

---

### Post by stinkeye on 2011-05-15
You can also install by creating a
**~/.cairo-clock/themes** directory
and place the extracted folder in ~/.cairo-clock/themes

---

