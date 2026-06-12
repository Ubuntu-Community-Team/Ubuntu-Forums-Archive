---
title: "Totem codecs and errors...."
date: 2005-07-28
forum: Desktop Environments
---

### Post by duran on 2005-07-28
I found a post with a link detailing the installation of codecs and began following the instructions. 

([http://www.ubuntuforums.org/showthread.php?t=51829&highlight=decoders+found](http://www.ubuntuforums.org/showthread.php?t=51829&highlight=decoders+found))

Some of the commands returned an error, example:

> toby@ubuntu:~$ sudo apt-get install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.8-lame 

Although this happened with several packages, I continued.  Of course, Totem didn't work when all was said and done.  When I try to play a movie, it returns the error that it couldn't play the file because "Could not open resource for writing".

I'm at a complete loss and any help that anyone could provide would be appreciated.

---

### Post by Sam on 2005-07-28
Did you [add extra repositories](ubuntuguide.org/#extrarepositories) ?

---

### Post by duran on 2005-07-29
Yes, I followed those instructions as well.

---

### Post by abrouwers on 2005-07-29
OK...once you've added the extra repositories, you must:

sudo apt-get update

Once it's done, you should be go to install.

---

### Post by duran on 2005-07-29
I didn't mention a potentially important bit of information - I'm running an AMd64.  I read elsewhere that not all packages are available to download for the 64bit Ubuntu which I'm running.  Does this explain why I would get errors saying it couldn't find certain packages?

If this is indeed the issue, can I run the 32bit version of Ubuntu on an a64, or do I have to run the 64bit?

thanks in advance.

---

### Post by dtfinch on 2005-07-29
I had always seen totem as a sort of empty shell of a media player, like a mockup GUI, but with errors. By default it's associated with hundreds of media file types it does not support. I have not found a single file it can play in the default configuration. It won't even play oggs, but it's associated with them. I know could just search around for a while and install the codecs, but most users would look at it and say "what the hell?"

---

### Post by bored2k on 2005-07-29
Are you running totem-xine or totem-gstreamer ? -xine is quite different.

---

