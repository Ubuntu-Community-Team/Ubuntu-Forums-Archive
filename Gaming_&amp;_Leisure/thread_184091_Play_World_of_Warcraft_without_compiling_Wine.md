---
title: "Play World of Warcraft without compiling Wine"
date: 2006-05-29
forum: Gaming &amp; Leisure
---

### Post by eqisow on 2006-05-29
I have compiled Wine debian files with the World of Warcraft patch already included. I have updated the following Wikis to reflect this:

[https://wiki.ubuntu.com/Wine]("https://wiki.ubuntu.com/Wine")
[https://wiki.ubuntu.com/WorldofWarcraft]("https://wiki.ubuntu.com/WorldofWarcraft")

You can find the package at the following mirror:

[http://thepiratecove.org/files/wine-0.9.14_wow_i386.deb]("http://thepiratecove.org/files/wine-0.9.14_wow_i386.deb")

I will keep these mirrors and the Wiki up-to-date as new versions of Wine are released.

Note: If these files end up getting popular, I don't know if my servers will hold. More mirrors would be appreciated.

---

### Post by Perfect Storm on 2006-05-29
If needed and people say it works. We can host them at Ubuntu Gamer's Arena.

---

### Post by Brainlessbob on 2006-05-29
This dont work for me.
When I try to run wine-0.9.14_wow_i386.deb it halts before installing and give me this.

brainlessbob@smeggingpie:~$ sudo dpkg -i wine-0.9.14_wow_i386.deb
Selecting previously deselected package wine.
(Reading database ... 124338 files and directories currently installed.)
Unpacking wine (from wine-0.9.14_wow_i386.deb) ...
dpkg: dependency problems prevent configuration of wine:
 wine depends on libartsc0 (>= 1.5.2-0); however:
  Version of libartsc0 on system is 1.4.3-0ubuntu1.
 wine depends on libasound2 (>> 1.0.10); however:
  Version of libasound2 on system is 1.0.9-2.
 wine depends on libgcc1 (>= 1:4.0.2); however:
  Version of libgcc1 on system is 1:4.0.1-4ubuntu9.
 wine depends on libglib2.0-0 (>= 2.10.0); however:
  Version of libglib2.0-0 on system is 2.8.3-0ubuntu1.
 wine depends on libstdc++6 (>= 4.0.2-4); however:
  Version of libstdc++6 on system is 4.0.1-4ubuntu9.
 wine depends on libxml2 (>= 2.6.24); however:
  Version of libxml2 on system is 2.6.21-0ubuntu1.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine

It says I got outdated packages but according to Synaptic I got the latest.
But since the maker of the file is Dapper tester and I use Breezy it may be the reason why it wont work.

---

### Post by Perfect Storm on 2006-05-29
True, would be neat if the dapper users can confirm if this package works.

---

### Post by JSM on 2006-05-29
Works perfectly on a day-old Dapper install.  Although I will admit that I couldn't get it working at all until I remembered I was in an XGL session :p

---

### Post by eqisow on 2006-05-29
Aye, this package is probably Dapper only. Unfortunately, I don't really have access to a Dapper box without making a new partition for it, but if somebody wants to make a Breezy package I'll be happy to host it as well. Pretty much everybody should be on Dapper in a few days though. :)

For now I'll just make a note on the Wiki that it's Dapper only.

Edit: Just out of curiousity, does anybody know the reason that this patch has yet to be merged into the main source tree? It's been available for several releases now, and I've never had experience with it breaking anything else.

---

### Post by sgtBiafra on 2006-06-05
The debian package worked like a charm. Thanks eqisow!

---

### Post by ELD on 2006-06-05
[QUOTE=eqisow]
Edit: Just out of curiousity, does anybody know the reason that this patch has yet to be merged into the main source tree? It's been available for several releases now, and I've never had experience with it breaking anything else.[/QUOTE]

If you read the latest wine newsletter they do talk about it.

---

### Post by GmAz on 2006-06-07
Make sure you install the libartsc0-dev from the Synaptic Package Manager!

---

