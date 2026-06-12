---
title: "Kaffeine will not play certain ´encrypted´ DVDs?"
date: 2005-08-23
forum: Desktop Environments
---

### Post by notmatt on 2005-08-23
Hi all

I can play most DVDs quite happily.  So I was pretty shocked the other day when after a long day of exams I popped in one of my Red Dwarf DVDs for some r and r and Kaffeine gave the following error:

```

The source seems encrypted, and can't be read. 
Your DVD is probably crypted. According to your country laws, you can or can't use libdvdcss to be able to read this disc. (Media stream scrambled/encrypted)

```

It plays happily in other DVD players (VLC), but has no sound.  The intro to the DVD plays with sound in Kaffeine, then gives me the message.

I have the libdvdcss2 package.  I have installed all other codecs and the like as per the ubuntuguide website.  I have poked around on the Kaffeine website and also on google, But not found anything yet, anyone got any more avenues to explore?

---

### Post by Takis on 2005-08-23
Nooooo! You gotta be able to play Red Dwarf! You'll make Mr Flibble cross, and who would clean up the mess?  :)

So is it just those Red Dwarf DVDs?

---

### Post by notmatt on 2005-08-23
[QUOTE=Takis]Nooooo! You gotta be able to play Red Dwarf! You'll make Mr Flibble cross, and who would clean up the mess?  :)

So is it just those Red Dwarf DVDs?[/QUOTE]

I will have a look through my rather small collection and see.  

<edit>
Neither of the Red Dwarf DVDs work.  Everything else is fine.

---

### Post by Takis on 2005-08-25
Send them back and ask for replacements!

Ask for the rest of the seasons, while you're at it.

---

### Post by notmatt on 2005-08-27
[QUOTE=Takis]Send them back and ask for replacements!

Ask for the rest of the seasons, while you're at it.[/QUOTE]
 Hmmm, you are really quite nuts aren't you?  I like it.

The DVDs are my girlfriends, she lent them to me over my exams to cheer me up.  Not really able to return them.  Guess I am going to have to get mplayer working.

---

### Post by notmatt on 2005-08-27
Could a mod please delete this double post.

---

### Post by notmatt on 2005-08-27
Could a mod please delete the double post.

---

### Post by guice on 2005-09-05
In all seriousness, is there a way to fix this? I'm getting the same problem, too. I hadn't tested other DVDs yet. I just popped in a random DVD (for testing) and got this error.

Is there some region code problems I need to fix? I am in Region 1 using a region 1 DVD.

*Edit; I tried a few more, same proble. Heck, I even threw in the first DVD I ever bought (from '95) and I still get the same error...

---

### Post by gnutux on 2005-09-05
ok, depending on your contry, you can install libdvdcss2 on apt-get, a country like Canada allows it, as far as I know.

gnutux

---

### Post by guice on 2005-09-05
[QUOTE=gnutux]ok, depending on your contry, you can install libdvdcss2 on apt-get, a country like Canada allows it, as far as I know.

gnutux[/QUOTE]
 libdvdcss2 doesn't show up on apt-get:```
root@kiler:~ # apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
root@kiler:~ # apt-cache search libdvdcss2
root@kiler:~ # apt-cache search libdvdcss
libdvdread3 - Simple foundation for reading DVDs
libdvdread3-dev - Simple foundation for reading DVDs
root@kiler:~ # apt-cache search libdvd
gstreamer0.8-dvd - DVD plugin for GStreamer
libdvdnav-dev - The DVD navigation library, development package
libdvdnav4 - The DVD navigation library
libdvdread3 - Simple foundation for reading DVDs
libdvdread3-dev - Simple foundation for reading DVDs
root@kiler:~ #
```

And I've already installed *libdvdread3* with no luck. FYI, I'm in the US.

---

### Post by Takis on 2005-09-05
[QUOTE=guice]libdvdcss2 doesn't show up on apt-get[/QUOTE]
Have you added the backports repositories to your sources.list?

---

### Post by guice on 2005-09-05
I found out how to get it. After a number of search on google, I found an old post from a newsgroup archive that said after installing libdvdread3 read the following file /usr/share/doc/libdvdread3/README.Debian

That file contained a path to a script that downloads and installs libdvdcss2.

---

### Post by Takis on 2005-09-06
[QUOTE=guice]I found out how to get it. After a number of search on google, I found an old post from a newsgroup archive that said after installing libdvdread3 read the following file /usr/share/doc/libdvdread3/README.Debian

That file contained a path to a script that downloads and installs libdvdcss2.[/QUOTE]
Word of advice: I had a look at the script the readme points out, it uses a Debian .deb file. Keep in mind that Debian .debs and Ubuntu .debs are not necessarily compatible - avoid downloading any .deb file that is not explicitly marked as for Ubuntu.

---

### Post by notmatt on 2005-09-07
I have already installed libdvdcss2.  It is only certain DVDs, not all.

Guice - you will probably have to put some 'non-us' repositories on your list.

---

### Post by guice on 2005-09-07
[QUOTE=Takis]Word of advice: I had a look at the script the readme points out, it uses a Debian .deb file. Keep in mind that Debian .debs and Ubuntu .debs are not necessarily compatible - avoid downloading any .deb file that is not explicitly marked as for Ubuntu.[/QUOTE]
 Where would you suggest one to get the Ubuntu package? libdvdcss2 isn't obtainable via apt-get for me, as I pointed out earlier.

---

### Post by notmatt on 2005-09-07
It should be tho' providing you add the correct repo.  What ones do you have down atm?

This is a different problem to the one I am having tho, I only have problems with specific DVDs, which obviously have different methods of encrytion.

---

### Post by Takis on 2005-09-07
[QUOTE=notmatt]It should be tho' providing you add the correct repo.  What ones do you have down atm?[/QUOTE]
Heh heh heh. In English, could you please post the contents of /etc/apt/sources.list ?

Thanks.

---

