---
title: "Default Browser not working"
date: 2009-05-19
forum: General Help
---

### Post by drhiii on 2009-05-19
Hi All,

Have searched for solution but not found so far...

Firefox is the default set in Preferred Applications.  I changed it to SeaMonkey.

Whenever I click on an outside link, like from a desktop icon, Firefox continues to load.  I create desktop icons directly out of Seamonkey, and same thing.  

Am scratching head to figure out how to get Seamonkey to launch as the Preferred App.

Ideas anyone?

tx all

---

### Post by KhurramM on 2009-05-20
Try the command option to use seamonkey in Preferred Applications

Hope this helps u.

OR goto:

gconf-editor

Desktop > gnome> app. > browser > change firfox to seamonkey cmd

---

### Post by drhiii on 2009-05-20
> **KhurramM said:**
> Try the command option to use seamonkey in Preferred Applications

Hope this helps u.

OR goto:

gconf-editor

Desktop > gnome> app. > browser > change firfox to seamonkey cmd


Thank you for your response.  I did use Custom Command Option in Preferred Applications and it failed, continuing to bring up Firefox.

Went to gconf-editor and followed your instructions.  The exec application was already set to Seamonkey.  Don't want to do this but am wondering what would happen if I uninstalled Firefox?  I don't want to go this route because, well, why.  But sure is a head scratcher.

Perplexing, because everything says it should run Seamonkey, but it brings up Firefox instead.

Anyone else?  Have you seen this behavior before?  Ideas?  Help help??

tx

---

### Post by drhiii on 2009-05-20
Here is one further piece to the puzzle.  

I selected Konqueror, Opera and Seamonkey as the Preferred Application for browser, and none of them worked.  No matter what I have done, selecting the individual program, or reverted to a Custom call, Firefox is the only browser that comes up when called from an outside program.

Anyone?

---

### Post by drhiii on 2009-05-20
And, more odd behavior.  

I found that if I drag and drop a URL from the little icon to the let of the URL address line onto a panel, it works.  I can click on it and it will bring up the appropriate selected browser in Preferred Applications.  But when I drag and drop same to the Desktop, it always defers to Firefox no matter what browser I have defined.  Also, I cannot drag and drop an icon from the panel to the desktop.  Thought I might trick it, but no go... that method still brings up Firefox.

Anyone have this behavior???

---

### Post by zika on 2009-05-20
did You try with putting /usr/bin/seamonkey in Custom line for preferred application?
did You LogOut after that change (not to say reboot) ... ? that might help. it is not necessary but it might do the trick ...

---

### Post by drhiii on 2009-05-20
> **zika said:**
> did You try with putting /usr/bin/seamonkey in Custom line for preferred application?
did You LogOut after that change (not to say reboot) ... ? that might help. it is not necessary but it might do the trick ...

Hello!  And thank you for your response.  Yes, I tried everything you mentioned.  Adding a absolute path in the Custom line.  Restarting after affecting changes.  Shutting down and restarting.  Everything.  No go.

The reason I think there is something squirrly is that it works when I drag and drop into the panel, but not into the desktop.  Me scratch head... 

Perplexed....

Thankx for the ideas.  Keep 'em coming.

---

