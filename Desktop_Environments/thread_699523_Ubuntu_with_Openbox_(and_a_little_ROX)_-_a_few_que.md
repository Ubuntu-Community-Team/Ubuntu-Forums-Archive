---
title: "Ubuntu with Openbox (and a little ROX) - a few questions...?"
date: 2008-02-17
forum: Desktop Environments
---

### Post by sajro on 2008-02-17
Hello!

I recently switched to OpenBox and I absolutely love it. However a big issue has come up: the menu. I ran "sudo update-menus" and it worked nicely but I want to edit the menu. However, when I open ~/.config/openbox/menu.xml and /etc/X11/openbox/menu.xml it mentions the menu package (which I used to generate) but does not have the full menu. The menu is there when I right click, the whole thing, but it's not in the source. How do I edit the menu? It's driving me crazy that there's a separate Apps and Applications.
 
Also, I'm wanting to use some lighter, faster ROX applications. I've got ROX-Filer but what others are available in the repos? Is there another repository (or repositories) where I can apt-get ROX apps so I can use things like Picky? 

Thanks in advance!
~Sajro

---

### Post by urukrama on 2008-02-17
> **sajro said:**
> Hello!

I recently switched to OpenBox and I absolutely love it. However a big issue has come up: the menu. I ran "sudo update-menus" and it worked nicely but I want to edit the menu. However, when I open ~/.config/openbox/menu.xml and /etc/X11/openbox/menu.xml it mentions the menu package (which I used to generate) but does not have the full menu. The menu is there when I right click, the whole thing, but it's not in the source. How do I edit the menu? It's driving me crazy that there's a separate Apps and Applications.

You can easily create your menus with Menumaker. Download it [here]("http://sourceforge.net/projects/menumaker"), unpack the archive and move into the extracted directory with the terminal
```
tar xzvf ~/menumaker-0.99.7.tar.gz
cd ~/menumaker*

```
Run menumaker with the following command (this will not install menumaker, but just run it):
```
./mmaker OpenBox3
```
You should now have a full menu available. Note that menumaker will not overwrite existing menu.xml files. If you have already changed your menu.xml file, you&#8217;ll need to back it up, remove it, and then add the changes to the new menu.xml file menumaker created.

You can then use obmenu to edit your menu.xml file further.
 
> Also, I'm wanting to use some lighter, faster ROX applications. I've got ROX-Filer but what others are available in the repos? Is there another repository (or repositories) where I can apt-get ROX apps so I can use things like Picky? 

I'm not sure as I never use Rox, but have you looked at the [Rox desktop website]("http://roscidus.com/desktop/")? I'm sure the source code should be available there, and perhaps a link to some debs if you are lucky.

---

