---
title: "How do I complie syslog-ng with --enable-spoof-source?"
date: 2009-04-01
forum: General Help
---

### Post by marc_zw on 2009-04-01
Hi there,

I am trying to setup a syslog server that I can use to filter and forward messages to a second syslog server.  However I need to maintain the original sender ip address in the syslog message.  I believe to accomplish this I need to compile syslog-ng with the --enable-spoof-source option.

Can someone please tell me how I go about this?

Thanks

---

### Post by Alterax on 2009-04-27
> **marc_zw said:**
> Hi there,

I am trying to setup a syslog server that I can use to filter and forward messages to a second syslog server.  However I need to maintain the original sender ip address in the syslog message.  I believe to accomplish this I need to compile syslog-ng with the --enable-spoof-source option.

Can someone please tell me how I go about this?

Thanks

Sure!  Just had to do this myself.  Install the following packages:

```
sudo apt-get install build-essential fakeroot

```
Then snag the dependencies for syslog-ng
```

sudo apt-get build-deps syslog-ng
cd /usr/local/src
sudo apt-get source syslog-ng

```
Now we need to modify the rules a tad. Your version number may differ slightly; don't sweat it.
```

cd syslog-ng-2.0.9
cd tgzbuild
sudo nano configure_opts

```
append the item **--enable-spoof-source** to the end of the single line, save and exit.

So now it's time to build your package!

```
cd ..
sudo dpkg-buildpackage -rfakeroot -uc -b

```
Go back another directory, and the .deb file is your modified version.
install it with 
```

sudo dpkg -i syslog-ng_2.0.9-4.1_i386.deb

```

And here's mine.  I made it on the x86 architecture; feel free to use it if the above method doesn't appeal, or if you're just looking for a quick plug-and-chug.

---

### Post by ynr78 on 2012-05-17
What about Ubuntu 12.04 ?
The instructions wont work though...

---

### Post by oldos2er on 2012-05-17
Old thread closed, please start a new thread for your question.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

