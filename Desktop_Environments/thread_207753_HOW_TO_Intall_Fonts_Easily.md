---
title: "HOW TO Intall Fonts Easily"
date: 2006-07-02
forum: Desktop Environments
---

### Post by wozbk on 2006-07-02
I had searched on Google and on this Forum a bit and did not find a simple way to get new fonts installed and available on my Dapper laptop.

By combining some info gleaned from a few different sources I came up with this:

I figured out a fairly full proof (though mildly dangerous, as you login graphically as root for a little while) way of of installing fonts that most of your applications will “pick up”.

This is specifically for Ubuntu Dapper but should apply in whole or part to earlier versions of Ubuntu.

Go to System>Admin>Users and Groups and set the password for the root user, then go to System>Admin>Login Window>Security Tab>and check the box for “Allow Local System Admin Login”.

Logout and then graphically login as root, then navigate within your fonts folder located at /usr/share/fonts.

Then download all the .ttf fonts you like and extract them and place them in a folder in your Desktop called something like my-fonts-ttf.  This folder should just have all your .ttf files in it or you can nest them in their own folders if you are super orderly.  When you are done and have all your extracted .ttf's, drag your “my-fonts-ttf” folder into the “fonts” folder you already opened earlier.

Open a terminal window and type:
sudo fc-cache -f -v
(hit enter)

This will make sure your new fonts are loaded and able to be used in OpenOffice, Inkscape and most of the apps you have installed.

You can now disable the graphical root login if you are done installing all your fonts.

----------------------

Hope this helps make your Ubuntu system more viable for doing higher end typographic work.

---

### Post by lotheac on 2006-07-02
You shouldn't login as root. Try gksudo nautilus instead (or use the command line to move files around).

---

### Post by wozbk on 2006-07-02
[QUOTE=lotheac]You shouldn't login as root. Try gksudo nautilus instead (or use the command line to move files around).[/QUOTE]I am aware of that - that is why it is disabled.  Not everyone knows there way around the terminal, but I can trust myself to be careful while logged in as root.

I am going to get myself a little O'Reilly book on the commands, however until I ramp up I still want to be able to use a wider variety of fonts.

I am trying to essentially see if I can produce work of the same richness as I can with my Mac and Macrodobe tools on a P3 laptop with Dapper.

So far I have been pretty happy, though I am just going to take it one slow step at a time.

As an aside my life would be incredibly boring if I never did what I shouldn't :).

---

### Post by lotheac on 2006-07-02
[QUOTE=wozbk]Not everyone knows there way around the terminal[/quote]

Which is exactly why I suggested using 'gksudo nautilus'. It will open a file manager as root.

---

### Post by wozbk on 2006-07-02
[QUOTE=lotheac]Which is exactly why I suggested using 'gksudo nautilus'. It will open a file manager as root.[/QUOTE]I love it - that is exactly the command I was after.

Is there a list of these commands for newbies like myself that you would suggest? I could probably find one but I would defer to your experience in one that would be best for Dapper.

Man pages and the like are a little hard for me to digest unless I have also have some info written a little more plainly to accompany them.

---

### Post by lotheac on 2006-07-02
Well, I really don't know of a list, but a quick search of the wiki brought up [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands). Hope it helps.

---

### Post by fluffington on 2006-07-02
Why not just put the fonts in ~/.fonts?

---

### Post by ftavares on 2006-07-26
> **fluffington said:**
> Why not just put the fonts in ~/.fonts?

This is absolutely right. Just put your ttf files in this folder and the fonts will become immediately available in every application.

This is the best option if you don't mind that the fonts are only available for your user.

---

### Post by Shay Stephens on 2006-07-26
I have to deal with fonts quite a bit, and by far the quickest easy way is to create a .fonts folder in your home folder and copy the fonts to that new .fonts folder.

No fuss, no muss.

---

### Post by Jou Moer on 2006-08-04
> **fluffington said:**
> Why not just put the fonts in ~/.fonts?

4th day using Ubunto, so dont know much about these things.  How do you do this?  I have eventually found this folder however, I'm not able to copy/paste my fonts in there.

I have downloaded fonts to my desktop - they have .ttf and .fon extensions.  Now, how exatly do I get them in the Font folder so I can use it?

---

### Post by mwob on 2006-08-04
Hi,

Where is the "~/.fonts" folder? I am new to linuz so I have no idea what the tilda refers to...

---

### Post by rpw on 2006-08-04
@mwob,

~ is your home directory.

The . before the folder fonts (.fonts) means that the folder is hidden. So when you open your home-directory in Nautilus (Places/Home directory I think, since I'm german my desktop shows the german translations).

Anyway, you will not find the directory in your home-directory, you have to create it yourself. Just create a new folder (in Nautilus it must be in the menu "File / New Folder"), and give it the name .fonts (including the dot at the begining!).

rpw

---

### Post by mwob on 2006-08-05
Aha! It all becomes clearer! Thanks for the reply :)

---

### Post by chavo on 2006-08-05
Another advantage to using ~/.fonts is that with your /home on a separate partiton you will never have to reinstall the fonts. They will be there if you install another distro or happen to need a reinstall of k/ubuntu or whatever.

---

### Post by Psquared on 2006-08-06
Another way I just used was System-Preferences-Font-Details-Go to Fonts Folder. Then you can just drag and drop. I did rerun the fonts cache just to make sure. Everything seems OK.

---

### Post by stanz on 2006-08-06
Hey Fellow New Users,
[Wiki Page for New Users Network.]("https://wiki.ubuntu.com/NewUserNetwork")

Check out ALL the links, & read well...Join if it sounds good for ya!
Ask/Request classes on 'your' topic of need.
Start walking away from 'newbie' status.  :-\"
Me2...
And I make my own folders also..easy beans !

---

### Post by randell6564 on 2006-08-06
> **Psquared said:**
> Another way I just used was System-Preferences-Font-Details-Go to Fonts Folder. Then you can just drag and drop. I did rerun the fonts cache just to make sure. Everything seems OK.

I tryed to do that and was unable to because of file permissions I think.

So I logged in as root and changed permissions on my fonts folder and all went well, so I thought.

I CAN use those fonts now, but they also show up in System>Preferences>Theme>Theme Details>icons tab!  That cant be good can it?

---

