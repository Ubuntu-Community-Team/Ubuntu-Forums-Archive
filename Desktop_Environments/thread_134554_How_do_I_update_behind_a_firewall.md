---
title: "How do I update behind a firewall?"
date: 2006-02-22
forum: Desktop Environments
---

### Post by henryjo on 2006-02-22
Hi,

New to Ubuntu, but not to linux. I've just started a new job as a Secondary School
teacher and have been handed the job of setting up their Moodle server for use on their intranet. No problem installing off the CD-ROM and had it up in an hour or two. I have moodle running under Ubuntu on my laptop and have had no hassles with installing the updates and packages using Synaptic at home (except for the GPG BADSIG bug). However, the school runs a very secure environment, so secure in fact that it seems no one is able to grant the server I am using access the internet! And, no, they won't give me access to the massive tangle of firewalls they are using. And I don't have the time to work out what they have done anyway.

Being new to the Ubuntu and Debian universe, how can I make my laptop a repostitory for apt-get or Synaptic to access from this server? At school, I can hook them up to same hub, so access between the machines is actually under my control.

By mucking about with proxy settings and the like, I did manage to get the server to realize it needed about 88 package updates, and could get Firefox to access the files, but not apt-get or Synaptic. But I had to reconfigure the network and take it off the local "server" net. And the thing is an old Compaq brick that's about the size of my car, so hauling it off home is not an option I'm keen on.

Thanks for any help or pointers, 

Henry

---

### Post by roshan.s on 2006-02-22
I don't know if this is what you're looking for, but you might be interested in [this.]("https://wiki.ubuntu.com/AptMoveHowto")

Also, you might want to look at the apt-zip package in universe, as it might serve your needs better.

---

### Post by henryjo on 2006-02-22
Thanks, but the Ubuntu systems I am using are old. I burnt the distro CD on my Mac at home. The laptop ain't got a CD burner. I had a look at my /var/cache/apt/archives and it has been trimmed somewhat, so the moodle, php and mysql packages are not there anymore. All the recent stuff is though.

apt-zip looks like it might do the trick too. I was hoping I could find an "easy" way of cloning the software install (the latest list or updates and packages) from the laptop to the moodle server. Which of course doesn't have moodle on it yet.

Guess I'll have to do some work. I always liked "click and pray" rather actually understanding what I was doing. Hence the mac.

Cheers

---

### Post by slux on 2006-02-22
How easy are you talking about?  Replicating the laptop with something like replicator is an option, depending on your hard drive size a crude dd over the network with netcat might do it as well.

apt-zip sounds like a good idea if those don't fit the bill. Or, you could set up a complete ubuntu mirror on the laptop but that would be quite huge and most likely not as easy as you're looking for.

How all this could be easy on a Mac OS X installation escapes me, however.

---

### Post by henryjo on 2006-02-22
Err. I gave up running Ubuntu on an iMac. I just use it for burning CD-ROMs. The DVD's never worked on the Thinkpad I'm running ubuntu on. Looking at Synaptic, I can get a list of all installed software, as well as a complete history of what has been done (nice!). So I guess maybe I could just download everything and not install it? Then use apt-move. Oops. Didn't work. 

Actually, setting up a "local" Ubuntu mirror might be the go. I'll need to keep the software updated on the server at school. The laptop does have a spare 20 GB or so I left in case I ever needed to install the "other" OS.

---

### Post by GrumpyBob on 2006-02-22
I've installed Ubuntu behind my work firewall.  I couldn't use Synaptic to do updates until I edited /etc/apt/sources.list (you'll need to sudo it) to change all the repos from http addresses to ftp addresses.

Might that help?

Robert

---

### Post by Ramses de Norre on 2006-02-22
Isn't it possible to share the internet on your laptop and connect the server to it for the duration of the download? You can do that once in a month then to update it. (I'm assuming you have an internet connection to connect the laptop to.)

---

### Post by henryjo on 2006-02-22
Unfortunately no. Only traffic on port 80 is allowed. And that is sort of. Means https and stuff like that don't work. I have to go home to use the Ubuntu wiki!! 

Hopefully, they will work something out. Meanwhile I'll try and have a go at using apt-move. Unfortunately, I did clean out my /var/cache/apt/archive a couple of months ago.  I'm trying to "rebuild" the archive by reinstalling using synaptic and selecting the download only option. Same with apt-get. But some of the packages  (like php5) don't want to re-install. 

What a pain

Cheers!

---

### Post by henryjo on 2006-02-22
All connections at the school are heavily firewalled. Stuff just breaks using the apt-get and synaptic. I've tried looking at packet traces to try and see what is going on, but that gives me a real headache. Not having access to admin the firewall is another.

---

### Post by Ramses de Norre on 2006-02-22
How can they expect you to do your job when they don't trust you in going on the internet 10min/month to update the OS..
And I don't know that much about ports, but isn't port 80 the normal http? Isn't that port used when you share internet then?
Correct me if I'm wrong, I'm interested in knowing why that isn't possible:)

---

### Post by roshan.s on 2006-02-22
It seems to me that apt-move is right for you. If you don't have a CD burner on your laptop, you can go upto the "create ISO image" step, copy the resulting .iso image to your Mac, and burn it from there. Since the CD will contain the packages in your laptop's cache, it should have moodle and its dependencies. This is exactly what you want.

Another thing is that Synaptic uses only the normal HTTP requests on port 80 to archive.ubuntu.com to install pages, so if you're able to browse the web from your server, you should be able to use Synaptic. At the most, you may be using a HTTP proxy. If you are, you can tell Synaptic to use the same proxy by going to Settings > Preferences > Network.

Finally, the simplest way I can think of for achieving the goal is to run a HTTP or FTP server on the laptop (HTTP is probably more secure.) Assuming you have all the moodle packages and their dependencies on your laptop, go to /var/cache/apt/archives/ and run "dpkg-scanpackages . /dev/null | gzip > Packages.gz" . This will effectively make your apt cache a mini-repository. Then share the /var/cache/apt/archives/ directory using your web server. Connect your laptop to the server over a network, and add the laptop's address to your sources.list file. For example, if your laptop is at 10.0.0.42, add: "deb [http://10.0.0.42/archive](http://10.0.0.42/archive) ./" to your /etc/apt/sources.list file on the server. Then Reload your headers from synaptic, select the packages you need, and voila.

You might find [these]("https://wiki.ubuntu.com/PersonalRepositories") [pages]("https://wiki.ubuntu.com/PackageCDs") useful if you go the dpkg-scanpackages route.

Edit: I just remembered that your laptop's cache no longer has the files. In this case apt-zip is probably the way to go. You need to run apt-zip-list on the server, and have it generate the script. You need wget and tar to run this script, so you can probably do it on your Mac if those commands are available (I've never used a Mac). Copy the tar file back to the server and run apt-zip-inst. You'll need to look at the man page for details.

---

### Post by henryjo on 2006-02-22
Awsome!

Thanks for all the help. As we are doing this as a long term project, the idea of making my laptop a repository looks like the way to go. We may still sort out the firewall to make all of this a non-issue, but I think installing a fresh Ubuntu on a partition of the laptop and using it for testing and as a local repository should do the trick. 

ARRGH! Can't access wiki.ubuntu.com from inside the school. Will wait until tonight.

Cheers!

---

### Post by jchau on 2006-02-22
A trick will be to setup a server outside the school and use it to foward the connection.  You can do this with openssh (installed on the outside server) running on port 80 (the only port allowed).  

And you can ```
ssh -D 3128 username@YourServerAddressHere
``` to set up a proxy on localhost from the computer inside the school.  

Then configure your Synaptic to use your new proxy on localhost port 3128.  (I'm assuming that the proxy for Synaptic supports SOCKS servers. I never tested this.  If it fails, it is probably here).  

Now run stuff normally.  Anything using localhost port 3128 will have as much internet access as the server you set up outside your school. 

Another option is find proxy servers that run on port 80.

---

### Post by secular on 2006-04-26
I'm also in a school and couldn't update through synaptic.

I just followed the advice here to change http to ftp in the lines in my sources.list.

I verify that it works.

---

