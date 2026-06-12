---
title: "Run graphical application ON the REMOTE DESKTOP over SSH"
date: 2007-11-28
forum: Desktop Environments
---

### Post by zlochko on 2007-11-28
OK... to make the short story long: 
I have a colleague who has kind of a bad working/desk position. So when the boss walks in... he always looks at my colleague's monitor (who of course has Skype & bunch of other "forbidden" applications started, including nude women on his screen, everything BUT Eclipse). 
As you can see it's a sad, sad situation, and I believe we all sympathize with him.

Well the basic idea is this:
Since I am sitting directly oposit from him and can see when someone walks into the ocean, me and my colleagues got an idea to SSH on his machine, and start a simple script which would bring the 'gnome-about' application on his display so he would know that someone is coming and switch to his programming editor or UML diagrammer or OpenOffice or whatever. 

Unfortunately we can't find solution for this. We just can't find a way to SSH on his machine and then START A GRAPHICAL APPLICATION ALSO ON HIS DISPLAY.

Please take pitty in his situation and help me make his life easier.
Thank you!  
:lolflag:

---

### Post by Prospero2006 on 2007-11-28
Hello there, 
I run a ubuntu middle school computer lab, and I send popups to the whole room all the time. I can do things like start firefox on every machine in the room with a single script from my teacher desk. Here's how:
(I have a whole directory filled with scripts like this one, but with different functionality)



Let's assume the following:

192.168.1.10 = your co-worker's computers
Your coworker is logged in as 'frank'

You create a text file that looks something like this:
```

ssh 192.168.1.10  'export XAUTHORITY=/home/frank/.Xauthority DISPLAY=:0; firefox-bin;' &

```

The last command there, firefox-bin, will execute on his monitor. 
Of course, you'll need passwordless ssh set up.
Put an icon on your desk, and wham. Instant boss alert.

Pros

---

