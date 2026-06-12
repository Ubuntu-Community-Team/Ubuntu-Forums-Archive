---
title: "OLPC Sugar"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Frihet on 2006-08-30
Has anyone successfully built OLPC Sugar in Dapper?

I tried this --> [http://wiki.laptop.org/go/Sugar_on_Ubuntu_Linux](http://wiki.laptop.org/go/Sugar_on_Ubuntu_Linux)

I end up in an endless loop at this point in the wiki -->

During the building task you may get the following error:

error during stage configure of matchbox-window-manager:....[9/12]

This error happens because Ubuntu uses the automake 1.4 version in contrast with matchbox-window-manager which uses the automake 1.9 version. In order to bypass this error you can execute the following command:

sudo update-alternatives --config automake

You will get the following list with the asterisk being at the 1 selection

There are 3 alternatives which provide `automake'.
  Selection    Alternative
 +    1        /usr/bin/automake-1.4
      2        /usr/bin/automake-1.7
 *    3        /usr/bin/automake-1.9
Press enter to keep the default[*], or type selection number:

Here you should press the button 3 and the try again to build sugar.

I would really like to get this running with Dapper, but may have to whip up a Fedora 5 box to make it go.

---

### Post by PurplePenguin on 2007-01-02
I was interested in giving it a shot, too, to see what stage the development is at... but haven't been able to find much discussion about it.  

Your post is quite old now.  Did you manage to get it working?

---

### Post by Frihet on 2007-01-02
Yes. I did get it working.

I think the issue was related to bugs in the components I was downloading early along. aA month or so ago I could follow the recipe without exception to build and run Sugar.

I am not doing anything more with this now because I can't get a machine.

Just a note: After playing with Sugar for a while, I've come to wonder what it is for. Seems like a lightweight version something we already have would be better. Better in terms of functionality and in terms of skill development for children.

---

### Post by jobezone on 2007-01-02
Why don't you just use qemu and virtualize it (or something)? There's some page somewhere in [http://wiki.laptop.org](http://wiki.laptop.org) explaining all the details.

---

### Post by Palypup on 2007-01-10
I have tried the live CD and it boots but I can't get past the grub command line on the splash page.    Get the live CD here [http://olpc.download.redhat.com/olpc/streams/development/LATEST-STABLE-BUILD/livecd/](http://olpc.download.redhat.com/olpc/streams/development/LATEST-STABLE-BUILD/livecd/)

---

### Post by fuscia on 2007-11-13
got there with the second from the bottom choice - [http://olpc.download.redhat.com/olpc/streams/sdk/build1/livecd/](http://olpc.download.redhat.com/olpc/streams/sdk/build1/livecd/)

i just took a quick tour. here are some screenshots...


edit: so, how old are the kids who are getting this thing?

---

