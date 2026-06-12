---
title: "Ah, those tar.gz...."
date: 2009-07-24
forum: Desktop Environments
---

### Post by coredeal on 2009-07-24
I hope I am in the right Forum for my question. If not, I apologize, and maybe you want to redirect me to the right one. OK, here goes.



Ubuntu-Linux 9 is a great OS, no question about it. After years of submission to Windows this is a real relief. Especially now, since Ubuntu recognizes, printers, scanners, peripherals...marvelous.  A pleasure to use. But, there's a but : why is it so complicated to install a new software ? That I cannot understand. You get a tar.gz package (I think it's called Tarball), you unzip it (that's easy) and then you find yourself with a number of files none of which is an executable (apparently). Reading answers in this Forum, booklets on using Ubuntu, FAQs in different sites – to no avail, I can't find a clear routine to put all this files to work together. Would any of you guys give me a hand to understand what I have to do to make a piece of software work (specifically, and just to get familiar with the routine, I have downloaded “70718-Diskspace.tar.gz, a screenlet, unzipped it and now I sit on a bunch of files with extension .py or .svg  or .package, a directory called “themes” containing conf – great ! But since the package does not come with install instructions or a readme file I feel like navigating in the middle of the ocean with no rudder) ? I offer you my thanks for any time you may spare for me. And I don't give up the ship !

---

### Post by philcamlin on 2009-07-24
if its a screenlet go into the screenlets window and click install then select the file and there you go :popcorn:

---

### Post by kostkon on 2009-07-24
And [this is a great how-to]("http://www.psychocats.net/ubuntu/installingsoftware") on how to install software in Ubuntu in general.

But yes, it's a screenlet applet. You need to install the screenlet manager first using Synaptic. Then you will be able to install and load the applet you have downloaded.

---

### Post by decoherence on 2009-07-24
tar.gz is the suffix for a compressed archive, similar to a file named with a .zip suffix. What you do with a tar.gz, once you've expanded it, depends on what is in it. Shame on whoever put together that tarball for not including at least a README. Perhaps there are installation instructions elsewhere on the site where you got it? Maybe it's available from somewhere else? I have a policy of avoiding software that lacks documentation.

Generally if you want to install software, you go to Applications > Add/Remove. This will download and install packages with nothing more than a click of the button. It's the preferred method of installing programs, assuming the program you want has been packaged for Ubuntu and is available in its software repository.

Otherwise, you can try to find a 3rd party Ubuntu package in the internet. It will end with a .deb suffix.

There's no one good answer for 'what do i do with a tar.gz?' Whoever is distributing that particular .tar.gz should have given you that information.

---

### Post by coredeal on 2009-07-24
> **philcamlin said:**
> if its a screenlet go into the screenlets window and click install then select the file and there you go :popcorn:

Hi,

and thank you for your time. I'll do that.

---

### Post by coredeal on 2009-07-24
> **kostkon said:**
> And [this is a great how-to]("http://www.psychocats.net/ubuntu/installingsoftware") on how to install software in Ubuntu in general.

But yes, it's a screenlet applet. You need to install the screenlet manager first using Synaptic. Then you will be able to install and load the applet you have downloaded.


Hi,

you're right, it's a great site to get better acquainted with this topic. Thank you, also, for indicating the screenlet manager as a way to go. I appreciated your guidance and time.

---

### Post by coredeal on 2009-07-24
> **decoherence said:**
> tar.gz is the suffix for a compressed archive, similar to a file named with a .zip suffix. What you do with a tar.gz, once you've expanded it, depends on what is in it. Shame on whoever put together that tarball for not including at least a README. Perhaps there are installation instructions elsewhere on the site where you got it? Maybe it's available from somewhere else? I have a policy of avoiding software that lacks documentation.

Generally if you want to install software, you go to Applications > Add/Remove. This will download and install packages with nothing more than a click of the button. It's the preferred method of installing programs, assuming the program you want has been packaged for Ubuntu and is available in its software repository.

Otherwise, you can try to find a 3rd party Ubuntu package in the internet. It will end with a .deb suffix.

There's no one good answer for 'what do i do with a tar.gz?' Whoever is distributing that particular .tar.gz should have given you that information.

Hi,

and many thanks for your exhaustive reply. I'm beginning to understand how the system works. Rather complicated, though. But I treasure your suggestions and will go from there. Again, I appreciated your guidance and time.

---

### Post by aysiu on 2009-07-24
> **coredeal said:**
> why is it so complicated to install a new software ? It's not. It's quite easy. > You get a tar.gz package (I think it's called Tarball), you unzip it (that's easy) and then you find yourself with a number of files none of which is an executable (apparently). That's because a .tar.gz isn't how you're supposed to install software unless you are an expert and have some special situation in which you want to compile from source or unless you are using an obscure program that no one's ever heard of. > Reading answers in this Forum, booklets on using Ubuntu, FAQs in different sites – to no avail, Read this, then:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by coredeal on 2009-07-25
> **aysiu said:**
> It's not. It's quite easy.  That's because a .tar.gz isn't how you're supposed to install software unless you are an expert and have some special situation in which you want to compile from source or unless you are using an obscure program that no one's ever heard of.  Read this, then:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Hi,

and thank you for your suggestion. Which is a good one as I have seen in the website you indicated. I think the basic concept I have to assimilare , when moving to Ubuntu after years of handling Windows, is that the overall approach is different : what I find so different is that in Windows you have strict rules to follow for everything; in Ubuntu you have the "open source" paradigm that opens an immense field for experimentation and avails itself of a fantastically motivated community. Your whole attitude towards computing has to change, but this is not easy after years of "one way only". So, for me, the "natural" way of installing software was to recompose the downloaded file fragments. Now, and thanks to the help of you people who answered my query, I am starting to see everything under a different light. Thanks again.

---

