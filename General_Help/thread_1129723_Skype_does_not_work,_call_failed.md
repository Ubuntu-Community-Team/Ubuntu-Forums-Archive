---
title: "Skype does not work, call failed"
date: 2009-04-19
forum: General Help
---

### Post by g35celicaz on 2009-04-19
I just installed ubuntu 8.10 on my laptop yesterday and installed Skype by putting this command in the terminal window:

sudo apt-get install skype


When I tried to make a call it said this:

Problem with audio playback

So I went to this website: [http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/](http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/)

It said to put this command in the terminal window:

sudo apt-get remove pulseaudio 

Then to put this command:

sudo apt-get install esound 


They both worked successfully 


However the last command they said to do did not even work the command was this:

sudo rm /etc/X11/Xsession.d/70pulseaudio 

Now I cannot make any calls 

Please Help

 - Thanks

---

