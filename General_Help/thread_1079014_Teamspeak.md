---
title: "Teamspeak"
date: 2009-02-23
forum: General Help
---

### Post by RedSingularity on 2009-02-23
Does anyone know how to get sound and microphone working in teamspeak?  I am using Esound, not pulsaudio.

---

### Post by Meow27 on 2009-02-23
if anyone recommends Wine, i ask them to answer the question for teamspeak native to linux

---

### Post by RedSingularity on 2009-02-23
Nevermind i got it.  I just took off Pulseaudio and Esound and everything works fine.  BTW i am using the Native linux version.

---

### Post by Dante123 on 2009-08-03
I have found under 8.10 and 9.04 that to get Teamspeak to work under Ubuntu I have to do the following:

1.  Make sure mic is working with sound recorder first (my default setup needed tweaking and front mic boost, some switches enabled for my system setup)

2.  Install Teamspeak through add/remove programs.

3. Setup the teamspeak launcher on the desktop and edit it so that is runs "padsp teamspeak".

4. Kill Pulseaudio under System Monitor--->Preferences (I know this seems counter-intuitive since in step 3 we just told it to use padsp wrapper and then we kill pulseaudio in this step- but without doing this, there are choppy mic issues)

5.  Run teamspeak from launcher on desktop and all should be well.  Worked on my system anyway.

Hope this helps someone.  If is works for you please reply.

Take care!

---

