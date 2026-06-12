---
title: "mp3 support in MusicBrainz in amaroK for Dapper"
date: 2006-08-11
forum: Desktop Environments
---

### Post by JohnPhys on 2006-08-11
Hey all,

I've been searching around to find out how to enable the mp3 support for MusicBrainz in Dapper.  All of the posts point to that libtunepimp2c2a was not compiled with mp3 support, so that's the issue.  I can find threads saying to just do 

```
sudo apt-build --reinstall --force-yes install libtunepimp2c2a
```

and it should work.  A few questions I have from reading too many threads:

1)  Does this work with the final version of Dapper?  Some of the threads were quite old (before dapper was officially released), and I had to pull in apt-build since it wasn't installed by default.

2)  Will Ubuntu/synaptic/whatever want to pull back in the libtunepimp from the ubuntu repos and continually give me a "update this package" message when it checks for updates?

3)  The apt-build command wants to pull in a lot of stuff.  Will recompiling the libtunepimp2c2a package this way break anything?

4)  Is there another workaround that I haven't come across?

Thanks!

---

### Post by JohnPhys on 2006-08-12
Please, anyone?

---

### Post by maniacmusician on 2006-08-12
sorry john, looks like no one has come across your post that can answer those questions. for a better chance of it getting answered i would suggest bumping it when traffic is high. ie; between 8 - 10 pm EDT or 7 - 10 am EDT. that way there'll be a better chance that someone who can  help you will stumble across your post.

---

### Post by JohnPhys on 2006-08-13
I guess I'll try bumping it....now!

I'd really appreciate any help anyone can give on these questions.

---

### Post by PuleX on 2006-08-27
I think I'll try the rebuild method as described here: 
[https://launchpad.net/distros/ubuntu/+ticket/980](https://launchpad.net/distros/ubuntu/+ticket/980) 
[http://kubuntuforums.net/forums/index.php?topic=5803.new](http://kubuntuforums.net/forums/index.php?topic=5803.new)

---

