---
title: "Tried to replace FF2 with FF3 but..."
date: 2008-04-28
forum: Desktop Environments
---

### Post by Theif on 2008-04-28
It's my first post here , so hello everybody!

So how it was ...
1.I downloaded FF3(FireFox 3) beta 5 , extracted it in my temp folder , everything worked perfect.
2.Then I decided to use it permanently.But I knew if I remove FF2 with apt-get\synaptic other important packages will be removed too.That's why I just cp -rf /mytmpfolder/firefox /usr/lib , THAT was my mistake =(
3.When cp was completed I get everything how I wanted , but then I rebooted...First of all GNOME reported me about mistake in clock applet

The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet".:(

Then I noticed that evolution mail doesnt works too.It's trying to load for some time , but never starts.When I try to run it in terminal it reports

evolution: error while loading shared libraries: libnssutil3.so: cannot open shared object file: No such file or directory

4.What I've already tried to do:
 a) reinstall firefox2 with synaptic
 b) removed /usr/lib/firefox and installed firefox from reps
 c) find libnssutil3.so in FF3 directory and put it in /usr/lib/firefox

Nothing helped.
Any ideas how to fix it , without reinstalling Ubuntu?(Ive got 7.10)
THX!

---

### Post by sigve on 2008-05-19
I've experienced the exact same problems after trying to install FF3.rc1 the same way you did, but on a Hardy Heron 8.04 distro with pre-installed FF3.b5.
In addition to the problems you mentioned, I also encountered the following:

- SSL doesn't seem to work anymore (in thunderbird, pidgin etc..)
- For some reason Brasero won't run???

I don't know if all of these are linked to the attempt at installing FF3...?

---

### Post by sigve on 2008-05-20
Alright!

This worked for me: I copied libnssutil3.so and all other files named lib* in the firefox-directory:
libfreebl3.chk  libmozjs.so  libnssckbi.so   libplc4.so    libsoftokn3.chk  libssl3.so
libfreebl3.so   libnspr4.so  libnssdbm3.so   libplds4.so   libsoftokn3.so   libxpcom.so
libjemalloc.so  libnss3.so   libnssutil3.so  libsmime3.so  libsqlite3.so    libxul.so

to the following directory:

/usr/lib/

I'm not sure which file did the magic, but somehow it worked!

---

### Post by jonathanhowell on 2008-06-19
I had the same trouble with Gutsy when I upgraded to FF3:

The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet".
Pidgin would not connect to server "Server requires TLS/SSL"

 I tried your suggestion {sudo cp /usr/lib/firefox/lib* /usr/lib/} and it magically fixed the trouble. SSL errors & everything!

Thanks!
- Jonathan

---

