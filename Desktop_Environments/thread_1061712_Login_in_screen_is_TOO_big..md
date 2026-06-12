---
title: "Login in screen is TOO big."
date: 2009-02-06
forum: Desktop Environments
---

### Post by rath3r on 2009-02-06
Hello,

The problem is the font on my login screen is huge. I can only see big circles and the bottoms of letters when typing my username and password. I attempted to fix this by editing the /etc/gdm/gdm.conf however then I could only see approx 1/4 of the screen and could not see the buttons at the bottom at all. What I had done was.

After the [server-standard] section I changed "-command=/usr/bin/X -br -audit 0". To read "-command=/usr/bin/X -br -audit 0 -dpi 96". As recommended in another post

This did not help as after restarting the X window did not restart and asked me to change screen resolution but would not change it. I used a Live CD to remove "-dpi 96". I could restart the computer however the problem still persists and there has been changes to my normal desktop moved buttons etc.

your assistance is appreciated I've searched the forums but cannot find the answer so I defer to your immense collective wisdom.

thanks,
rath3r

p.s. I'm using Hardy (8.04.2)

---

### Post by trellis2 on 2009-02-07
Rath3r Try this:

Steps to force 96DPI fonts:

1) Select 'Administration' from the 'System' menu
2) Select 'Login Window'
3) Select the 'Security' tab
4) Click on the 'Configure X-Server' button at the bottom of the screen
5) Append this argument to the text in the 'Command' text-field: '-dpi 96' (Without the ' marks)
6) Restart your X session ( Ctrl+Alt+Backspace)to see the changes.

" a horn toot for  Barry Carroll, written on 2007-04-21, may all his Halley Berry fantasies come true."

---

### Post by LarsO on 2009-02-21
The 96 dpi did not solve it for me. It has been a problem for me with 8.04 on many different computers and finally stumbled upon a solution that does work:
[http://insidesocal.com/click/2008/06/ubuntu-fix-login-screen-too-bi.html](http://insidesocal.com/click/2008/06/ubuntu-fix-login-screen-too-bi.html)

Basically change the virtual resolution to your desired resolution. 

Section "Screen"
       Identifier               "Default Screen"
       Monitor                 "Configured Monitor"
       Device                   "Configured Video Device"
       Defaultdepth           24
       SubSecton "Display"
              Depth   24
              Virtual 1280      960      <--- change this to the right res.

---

