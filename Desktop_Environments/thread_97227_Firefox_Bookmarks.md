---
title: "Firefox Bookmarks"
date: 2005-11-30
forum: Desktop Environments
---

### Post by Rios on 2005-11-30
Hi,

I'm pretty knew to Linux so please be gentle and I'll apologise in advance if this question is really dumb!  :eek: 

I've been using Ubuntu Hoary for a while.  I'd managed to transfer my email, internet and MSN stuff across from my Windows machine and was happy.  Until the other day when I couldn't use it as it kept telling me that my "Gnome-Panel" had terminated.  This repeated for ever...  It's now got to the stage where it won't even boot up!

So, I decided to use a spare hard disk and install Badger instead which I'd been trying to pluck the courage up to install for a few weeks.  I've mounted my old main disk and I've managed to transfer everything but I cannot find my Firefox bookmarks.  Of course I didn't export them to back them up, so my question is... are they stored somewhere in a similar fashion to IE bookmarks?  And if so where and how do I install them on my new Firefox?

Many Thanks and all help will be much appreciated.

---

### Post by taurus on 2005-11-30
It should be in ~/.mozilla/firefox/"!!!!!".default/bookmarks.html (replacing !!!!! with the actual numbers and letters from your system...

---

### Post by Rios on 2005-11-30
Hmm, I don't have a directory /.mozilla/firefox   I have a /usr/mozilla/firefox but the bookmarks.html in there is just the default one.

I've searched for all "bookmarks.html" and it brings up a few but they all seem to be standard Firefox ones, not my bookmarks.

Any other suggestions please?

---

### Post by taurus on 2005-11-30
You have used firefox with your regular account before and saved all those links in your Bookmarks, right!  Again, it's not /.mozilla/firefox; it's ~/.mozilla/firefox...

---

### Post by Rios on 2005-11-30
Cheers Taurus, I get you now and you were spot on.  Funny how a little squiggle can mean so little to those who haven't a clue!

I owe you a beer.

;)

---

### Post by taurus on 2005-11-30
No problem.  Just so you know, ~ means $HOME or your home directory.  Therefore, ~/.mozilla/firefox means /home/phoenix/.mozilla/firefox (on my system)...  ;)

---

### Post by Danielle on 2005-12-01
hi, can someone help me find my home directoy, please? i'm trying to find my Firefox bookmarks also a program i just installed is supposed to be there too but i can't seem to find it.

i have tried looking in home/user name - the folder with the custom home icon but that can't be the home directory because my firefox bookmarks aren't there and the program i just installed isn't either. please help me before i throw the computer out the window.

---

### Post by aysiu on 2005-12-01
Your Firefox bookmarks and all of you Firefox settings are in /home/danielle/.mozilla

.mozilla is a hidden folder, however. So if you press Control-H while in /home/danielle, you'll see it.

As for the program you installed.. what program was it? It's probably not in your /home folder. It's probably in /usr/bin, but you don't need to know where it is--you can just launch it with the application name. For example, if you install K3B, you just open up the Run command (Alt-F2) and type ```
k3b
```. If you install AbiWord, just open up the Run command and type ```
abiword
```.

---

### Post by Danielle on 2005-12-01
thanks for helping me, aysiu. i thought i was going mad :rolleyes: can you tell me how to enable that ctrl-h setting all the time? i understand what it means so i'll be careful. and i think the hidden folders have a dot infront of the name.

i found the program it's called pogo and it's an application launcher. here's the page for it:
[http://www.ibiblio.org/propaganda/pogo/](http://www.ibiblio.org/propaganda/pogo/)

i'm so happy it was hidden and not lost :rolleyes: 

do you have any idea how to run pogo, pogo isn't correct :( here's a screenshot of pogo's folder and inside the scripts' folder too.

---

### Post by Danielle on 2005-12-01
[color=red]EDIT[/color]
hi, i worked out the bookmarks i imported them to Opera. i just need to workout how to launch pogo now. and how to enable hidden foldders for good.

---

### Post by aysiu on 2005-12-01
[QUOTE=Danielle]thanks for helping me, aysiu. i thought i was going mad :rolleyes: can you tell me how to enable that ctrl-h setting all the time? i understand what it means so i'll be careful. and i think the hidden folders have a dot infront of the name.[/quote] See attached screenshot.

> 
i found the program it's called pogo and it's an application launcher. here's the page for it:
[http://www.ibiblio.org/propaganda/pogo/](http://www.ibiblio.org/propaganda/pogo/)

i'm so happy it was hidden and not lost :rolleyes: 

do you have any idea how to run pogo, pogo isn't correct :( here's a screenshot of pogo's folder and inside the scripts' folder too. I don't know how to launch pogo. If it's not installed through the repositories, it's on a case by case basis.

**Edit**: According to the installer file text, *Pogo's executable files have been copied to your home directory..To run Pogo, type '/root/.pogo-3.0/pogo*

> 
hi, i want to import my firefox bookmarks to Opera but when i do it it just imports the default books. atm i have them on my desktop, i was thinking of cutting and pasteing them to the place firefox keeps it's default book marks:
/etc/mozilla-firefox/profile/bookmarks.html

what would the command be to move the bookmarks from the desktop to the folder above? thanks What do you mean it just imports the default bookmarks? I'm not sure what you mean. When I important Firefox bookmarks to Opera, it imports all of them to a folder called Netscape bookmarks. You cannot just copy and paste the bookmarks--they are not stored the same way.

---

### Post by Danielle on 2005-12-02
[QUOTE=aysiu]See attached screenshot.

 I don't know how to launch pogo. If it's not installed through the repositories, it's on a case by case basis.

**Edit**: According to the installer file text, *Pogo's executable files have been copied to your home directory..To run Pogo, type '/root/.pogo-3.0/pogo*

 What do you mean it just imports the default bookmarks? I'm not sure what you mean. When I important Firefox bookmarks to Opera, it imports all of them to a folder called Netscape bookmarks. You cannot just copy and paste the bookmarks--they are not stored the same way.[/QUOTE]
hi, i just wrote a reply and when i clicked submit i wasn't logged in so it's gone :(

i managed to fix the bookmarks :) and i managed to show hidden files too.

thanks for all your help, aysiu. but, there's no pogo in the pogo folder to launch. i had a look at the icons and i don't like the look of the program. there were no screenshots for it so i had no idea, i'm really sorry but i want to uninstall pogo. i tried cding to the directory and runinng:
sudo make uninstall
but 
there's no uninstaller, can i delete the folder? what would the command be? thanks and sorry for wasteing your time :(

---

### Post by aysiu on 2005-12-02
Unfortunately, there's no easy way to uninstall programs that have their own installer scripts. It's not even a ./configure make make install install from source.

Your best bet is just to locate all the pogo files and delete them. I'm sorry, but that's the best I can think of.

---

### Post by Danielle on 2005-12-02
thanks, aysiu O:)  i just deleted the folder

---

### Post by mcduck on 2005-12-02
Open nautilus, then go to edit/preferences, and on the 'views'-tab mark 'Show hidden and backup files'

Edit: by the way, you can import/export your bookmarks with firefox. Just go to bookmarks/manage bookmarks, then click on 'file' and there are options to import and export your bookmarks. Many firefox extensions also have their own import/export features.

---

### Post by Danielle on 2005-12-02
[QUOTE=mcduck]Open nautilus, then go to edit/preferences, and on the 'views'-tab mark 'Show hidden and backup files'

Edit: by the way, you can import/export your bookmarks with firefox. Just go to bookmarks/manage bookmarks, then click on 'file' and there are options to import and export your bookmarks. Many firefox extensions also have their own import/export features.[/QUOTE]
thanks, mcduck. i've got everything fixed now, well all the stuff in this  thread anyway :D

---

