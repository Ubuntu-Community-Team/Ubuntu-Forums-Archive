---
title: "Sharing Mac OSX printer"
date: 2005-12-31
forum: General Help
---

### Post by Apostata on 2005-12-31
Hello,

  I'm trying to have my wife's HP printer shared to our common LAN. She runs Mac OSX and has SMB support on (as well as Printer Sharing).
  I set it up on my end (SMB via CUPS -> IP address -> printer type etc.), but cannot print successfully. Print jobs do not show errors, but rather hang idle indefinitely. 
 I know her networking settings are correct, as my iBook can print to her HP Printer over the network. The fact that I was able to do this on the iBook seems to prove that it's not a user/password situation - I was never prompted for one using the iBook.

  I've got Samba, but I'm having a hell of a time trying to run 'swat'.  As per other discussions in the forum, I edited my inted.conf file to allow swat to run.  I still get an error when I try to open 'http://localhost:901/' in my browser. Samba daemon is running at startup.
 
 Has anyone else been in this situation?  Any help appreciated - it's a stumper.

---

### Post by Apostata on 2006-01-04
Here's the solution:  don't set it up in KDE.

I've spent bloody days trying to figure out the proper syntax of the host address etc. using the KDE 'print wizard'.  Then, following the cue of a webpage on CUPS config, I decided to see if GNOME was any easier.

It took about 5 minutes.  Administration -> Printing.  Enabled LAN printer search, and sure enough the bugger showed up and works perfectly.

One of the many reasons why I like having KDE and GNOME side by side.

---

### Post by ipaidforthisname on 2006-01-04
[QUOTE=Apostata]Here's the solution:  don't set it up in KDE.

I've spent bloody days trying to figure out the proper syntax of the host address etc. using the KDE 'print wizard'.  Then, following the cue of a webpage on CUPS config, I decided to see if GNOME was any easier.

It took about 5 minutes.  Administration -> Printing.  Enabled LAN printer search, and sure enough the bugger showed up and works perfectly.

One of the many reasons why I like having KDE and GNOME side by side.[/QUOTE]

I had a similar situation tonight. I ended up doing the exact same thing you did. I can't say I'm terribly fond of the KDE 'print wizzard'.

---

