---
title: "Best Terminal Apps??"
date: 2007-06-14
forum: Desktop Environments
---

### Post by jseiser on 2007-06-14
I have just a server install and fluxbox on this computer, its now old, or slow or anything i just have to get the most out of it because.. i guess im like that :)

i found k mandlas blog, which is awesome and has helped my linux experience a lot.  From his blog i found some terminal apps that quickly and simply do what i need.  Are there any other apps that would help fit into my desktop?


music player - cplay
torrents - rtorrent (wish it had encryption :/ )
file manager - mc  (wow, it seems im more in control with this than thunar/nautilus)
editor - nano
system info - htop   
volume -alsamixer
web - elinks (firefox for flash :( )
image viewer- feh (also sets background right from flux-menu)


this desktop seems to be working really well, and i havent had the need to use anything that isnt on a terminal besides Firefox, which is ugg but another story :)  I cant really seem to think of any thing else i might need to do on the computer.  I wish i could run htop at all times transparently but i cant seem to use the nvidia drivers unless i do a full u/x/k/buntu install which doesnt really seem worth it.  Is there ANYTHING i am missing out on that most people do?  almost wish i could split terminals acrossmy screen and just use that, i cant seem to find a reason for not using a terminal app besides firefox. Please post some tips, comments and more applications or maybe even a window manager/distro  that i would want to try.  Thanks, and sorry for the rambling :)

---

### Post by llamakc on 2007-06-14
mutt -- for your mail user agent.
screen - for detachable sessions

---

### Post by RedSquirrel on 2007-06-14
crip - for ripping.

---

### Post by muximus on 2007-06-14
i prefer pine fr mail, good ol mpg123 for music, vim fr text editing and elinks fr browsing.. tht is all tht i need mostly

---

### Post by llamakc on 2007-06-14
apt-get install vowel

j/j

---

### Post by Nythain on 2007-06-14
eterm takes a bit to get used to but its a great terminal emulator with psuedo transparency capabilities... many people use it as thier "desktop" terminal, basically setting it up to run border and title-less and "under" all thier other apps, pseudo transparent so it looks like its part of the desktop

multi-tail could be fun to play around with

pseudo transparency shouldnt require binary drivers since it just copies the section of the desktop it covers, creates a pixmap, and uses that as the background... only problem is if its on top of another app it looks kind of funny, like a big square hole through everything it covers, straight to your desktop

---

### Post by danhm on 2007-06-14
elinks and w3m are pretty good web browser for the terminal, you might want to give them a shot.

EDIT: Nevermind -- I seemed to have skipped over that section in your original post.

---

### Post by thePsychologist on 2007-06-15
I really like snownews. It's a feed reader for the terminal, and doesn't interfere with a transparent terminal. To me that's pretty important.

---

### Post by kerry_s on 2007-06-15
> **jseiser said:**
> I have just a server install and fluxbox on this computer, its now old, or slow or anything i just have to get the most out of it because.. i guess im like that :)

i found k mandlas blog, which is awesome and has helped my linux experience a lot.  From his blog i found some terminal apps that quickly and simply do what i need.  Are there any other apps that would help fit into my desktop?


music player - cplay
torrents - rtorrent (wish it had encryption :/ )
file manager - mc  (wow, it seems im more in control with this than thunar/nautilus)
editor - nano
system info - htop   
volume -alsamixer
web - elinks (firefox for flash :( )
image viewer- feh (also sets background right from flux-menu)


this desktop seems to be working really well, and i havent had the need to use anything that isnt on a terminal besides Firefox, which is ugg but another story :)  I cant really seem to think of any thing else i might need to do on the computer.  I wish i could run htop at all times transparently but i cant seem to use the nvidia drivers unless i do a full u/x/k/buntu install which doesnt really seem worth it.  Is there ANYTHING i am missing out on that most people do?  almost wish i could split terminals acrossmy screen and just use that, i cant seem to find a reason for not using a terminal app besides firefox. Please post some tips, comments and more applications or maybe even a window manager/distro  that i would want to try.  Thanks, and sorry for the rambling :)


opera is lighter than firefox
dillo is my normal browser
aterm is my terminal
xzgv for viewing pics, if i really want to cut space i just use dillo
emelfm is my filemanager in X, mc for no X
gv for pdf and ps
vlc for music, video

---

### Post by mcduck on 2007-06-15
ncmpc. My absolute favourite client for Music Player Daemon, and also the best music player I've ever tried. :)

I also like nano, links2 and MidnightCommander. And apt-get of course..

---

### Post by jseiser on 2007-06-15
thanks thanks, trying out some of these!

---

### Post by Nythain on 2007-06-15
> **mcduck said:**
> ncmpc. My absolute favourite client for Music Player Daemon, and also the best music player I've ever tried. :)

I also like nano, links2 and MidnightCommander. And apt-get of course..
wow... ncmpc is pretty sweet... im currently trying to build a desktop based on desktop terminals, and you just helped me with the curses mp3 player, thanks much

anymore terminal apps anyone recomends, and what they do... currently have mc for my file manager AND terminal, HTop for process management, conky for system info, and now ncmpc for mp3

---

### Post by Bill Cosby on 2007-06-16
IRC: irssi
Graphics: ImageMagick
Term: rxvt-unicode
Accounting: ledger
burning: cdrkit
p2p: rtorrent
music: mpd with ncmpd
video: mplayer

this is nice [http://enterprise.linux.com/search.pl?tid=89](http://enterprise.linux.com/search.pl?tid=89)

---

### Post by dustigroove on 2007-06-16
[FONT=Arial][SIZE=2][COLOR=Black]> **thePsychologist said:**
> I really like **snownews**. It's a feed reader for the terminal, and doesn't interfere with a transparent terminal. To me that's pretty important.

That's a very decent little RSS reader... thanks much!

Cheers

[/COLOR][/SIZE][/FONT]

---

### Post by kerry_s on 2007-06-16
"unp" for unpacking stuff, i can never remember the right commands to unpack the different packed types with "unp" i just type unp *.tgz, .bzip, .gz, etc...

"axle" multithread downloader like wget, but faster.

---

