---
title: "How Do I Add This Theme To Pidgin?"
date: 2008-12-06
forum: General Help
---

### Post by RookieUbuntuUser58 on 2008-12-06
[http://linux.softpedia.com/get/Desktop-Environment/Screenlets/Transparent-v2--Pidgin-Screenlet-theme-42818.shtml]("http://linux.softpedia.com/get/Desktop-Environment/Screenlets/Transparent-v2--Pidgin-Screenlet-theme-42818.shtml")

I need detailed instructions on how to configure it to work in a terminal. Still a newbie so don't really know how to go about installing the theme. The instructions on the page dont help either. Thanks in advance.


BTW if anyone knows about a black transparent Pidgin theme let me know. Thanks.

---

### Post by Solaris3k1 on 2008-12-06
First off, do you have the pidgin-screenlets package installed?  It's not an actual theme FOR pidgin, but rather a transparent theme for the pidgin screenlet (think a widget on Mac or Vista)

If you don't... you'll need to install it.  Here's a link to the pidgin-screenlet site on Gnome-look.

[http://www.gnome-look.org/content/show.php/PidginScreenlet?content=72611](http://www.gnome-look.org/content/show.php/PidginScreenlet?content=72611)

After that... go to your root directory... you won't need to use the CLI for this, although you could if that would make you more comfortable and I can walk you through that as well.

Once in your root directory, click on view, and then show hidden files.  Navigate to ~/.screenlets/pidgin/themes and then copy the files from the theme in there.  Once you've done that, let me know how it works.

Let me know how it goes.

---

### Post by RookieUbuntuUser58 on 2008-12-07
Thanks for the tips. I have to figure out how to extract the Pidgin screenlet and get it working. Then I would appreciate some help on the CLI method to installing the theme. Thanks again.

---

### Post by Wartender on 2008-12-07
ok, to extract the pidgin screenlet, open screenlets manager and drag the .tar(.gz) file onto the manager and it should install.
for the theme go to ~/.screenlets/pidgin/themes, (~means/home/username/, and you have to press ctrl+h to show the hidden files (that start with . ))and extract the folder (don't put the compressed file there, just the folder) and the theme should be there. (you might have to restart the screenlet.

---

### Post by RookieUbuntuUser58 on 2008-12-07
Thanks alot for the detailed instructions, that worked. I was trying to install through the terminal before and was getting stuck. Didnt know you had to install it through the screenlets.


One question though how do you scroll down in the Pidgin screenlet. All my buddies don't fit on the screen.

Also for the screenlet to work you have to have the Pidgin application running. Is there a option to set the Pidgin app to start with Ubuntu (from boot up)? I dont see that option, only for the Pidgin screenlet.

---

### Post by Wartender on 2008-12-07
you're welcome!
and i'm not sure about that, i've never had to scroll down the buddy list in the screenlet (actually i don't use it anymore) 
but as for making pidgin run on startup just go to system->preferences->sessions and click add and in the comand type pidgin .now it should start up immeadiately when you log on.

---

### Post by RookieUbuntuUser58 on 2008-12-07
Thanks that worked. Do you remember how you change your status in the Pidgin screenlet? Have to do it through the Pidgin application?

---

### Post by Wartender on 2008-12-07
yeah i'm pretty sure you have to do it through the application since the screenlet is just a buddy list (although you can also do it through the daemon in the top panel by right clicking it and going to change status, that way you don't have to open it and close it every time.)

---

### Post by fr0g on 2009-09-02
Just wondering..how do you access the screenlets manager? Also, where is the ~/.screenlets/pidgin/themes directory, can't seem to find it. 
Cheers.

---

