---
title: "What have I installed?"
date: 2005-03-24
forum: Desktop Environments
---

### Post by ioliver on 2005-03-24
I'm setting up a 2nd Ubuntu machine and would like to get it fairly close to the setup of my 1st.

As I've read these forums, I've often installed new stuff to fix various issues (adding codecs, different printer stuff, all sorts).  Is there a way to see a "diff" of what packages I have installed versus the Ubuntu Hoary standard install?

Ian

---

### Post by tonym on 2005-03-26
dpkg --get-selections will list all the packages installed.  You could run that on both machines and diff.

You could copy the details from your old machine and use dpkg --set-selections to upate your new machine to match.

---

### Post by Ozitraveller on 2005-03-26
It would be nice if it was possible to do automated installs with ubuntu. Another approach I've used with windows is to image the partition or drive with Norton Ghost and then put the image on another machine. This works best if the machines are identical (and I mean IDENTICAL!!).

Here are a couple of linux apps I've recently found that do the same thing:


[COLOR=Red]**SystemImager**[/COLOR] is software that automates Linux installs, software distribution, and production deployment.
SystemImager makes it easy to do automated installs (clones), software distribution, content or data distribution, configuration changes, and operating system updates to your network of Linux machines. You can even update from one Linux release version to another! 

It can also be used to ensure safe production deployments. By saving your current production image before updating to your new production image, you have a highly reliable contingency mechanism. If the new production enviroment is found to be flawed, simply roll-back to the last production image with a simple update command! 

Some typical environments include: Internet server farms, database server farms, high performance clusters, computer labs, and corporate desktop environments. 

[http://www.systemimager.org/](http://www.systemimager.org/)




[COLOR=Red]**g4u**[/COLOR] - Harddisk Image Cloning for PCs
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

Hope this helps. If anyone tried them I'd be interested in some feedback.

---

### Post by ioliver on 2005-04-05
> dpkg --get-selections will list all the packages installed. You could run that on both machines and diff.

Thanks, that looks like a great approach.

I guess it would be easy to produce a tiny shell script, which coupled with a file containing all the stuff that's in Hoary by default, would let me easily display new stuff.  The live CD is probably a good way to get this default list.

Ian

---

