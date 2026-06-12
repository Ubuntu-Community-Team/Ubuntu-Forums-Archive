---
title: "can I auto-mute 'line' channel when exiting tvtime?"
date: 2004-12-10
forum: Desktop Environments
---

### Post by darkfox on 2004-12-10
I use TVtime to watch telly, and the audio signal comes into my audigy soundcard via the line channel from a bttv card. All is well, apart from an annoying interferance noise from any screen activity when the telly is off but the line channel is still on.
     
 I am a recent convert to Ubuntu from Gentoo (I love Ubuntu - big hats off to all contributors for putting together such a well made bit of kit - really world class. It has permanently replaced Gentoo for me, and I'm even growing to love Gnome!). Before I switched I used KdeTV and within it there was an option to have the line channel muted by default when not in use. On opening the telly app it would unmute and remute itself when I closed the telly again. This is exactly what I want to do here (TVtime, Gnome 2.8, alsa). I have searched documentation but not found a hint. Can you help me?
     
     Thanks
     Andy

---

### Post by darkfox on 2004-12-11
Thanks entirely to the support of Rich Duzenbury, this has now been achieved. The solution is obvious to any of you beyond n00b status, but for those like me here's how to do it:
   
   1> Install aumix (a small soundcard mixer)
   2> Make the following script, ensuring that the file has execute permissions:
        #!/bin/sh
        aumix -l 100
        tvtime -t /tmp/TV.xml
        aumix -l 0
  3> When you want to start TVtme, execute the script rather than the application directly. In Gnome you can do this by right-clicking your TVtime icon, choosing 'properties' and changing the command (to for example in my case: '/usr/local/share/scripts/tvtime.sh')
   
  Finally this type of solution should work regardless of which TV app you use, provided the audio signal goes into your sound card via the 'line' channel.
   
   Thanks again Rich!

---

### Post by poptones on 2004-12-11
I just keep tvtime running on desktop 2 and mute the line in when I don't want to hear it. It requires few resources when it's not onscreen.

---

### Post by shamanu19 on 2007-05-15
spam

---

