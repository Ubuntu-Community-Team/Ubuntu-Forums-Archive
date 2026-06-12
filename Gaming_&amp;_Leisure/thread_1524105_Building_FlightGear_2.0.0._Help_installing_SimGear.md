---
title: "Building FlightGear 2.0.0. Help installing SimGear, please!"
date: 2010-07-04
forum: Gaming &amp; Leisure
---

### Post by Lauxmonster on 2010-07-04
Hello,

So FlightGear 2.0.0 got released a couple months ago. I didn't realize it because only 1.91 is in the repos/software center. 

So I downloaded the source stuff off the FlightGear website. Didn't realize what I was getting into. Whatever, had to install like 15 libs and all sorts of stuff.

Anyway, so I am brutally close to finishing the install. SimGear, the engine-like code that is the backbone to FlightGear needs to be installed. I just finished configuring it which took about 2 hours. So i did:

```
sudo make install
```

Thought it would work but it was plagued with errors. This is what I got:

```
george@dykstra-desktop:~/Downloads/SimGear-2.0.0$ sudo make
[sudo] password for george: 
Making all in simgear
make[1]: Entering directory `/home/george/Downloads/SimGear-2.0.0/simgear'
make  all-recursive
make[2]: Entering directory `/home/george/Downloads/SimGear-2.0.0/simgear'
Making all in xml
make[3]: Entering directory `/home/george/Downloads/SimGear-2.0.0/simgear/xml'
g++ -DHAVE_CONFIG_H -I. -I../../simgear -I../..    -g -O2 -D_REENTRANT -MT easyxml.o -MD -MP -MF .deps/easyxml.Tpo -c -o easyxml.o easyxml.cxx
mv -f .deps/easyxml.Tpo .deps/easyxml.Po
gcc -DHAVE_CONFIG_H -I. -I../../simgear -I../..    -g -O2 -D_REENTRANT -MT hashtable.o -MD -MP -MF .deps/hashtable.Tpo -c -o hashtable.o hashtable.c
mv -f .deps/hashtable.Tpo .deps/hashtable.Po
gcc -DHAVE_CONFIG_H -I. -I../../simgear -I../..    -g -O2 -D_REENTRANT -MT xmlparse.o -MD -MP -MF .deps/xmlparse.Tpo -c -o xmlparse.o xmlparse.c
mv -f .deps/xmlparse.Tpo .deps/xmlparse.Po
gcc -DHAVE_CONFIG_H -I. -I../../simgear -I../..    -g -O2 -D_REENTRANT -MT xmlrole.o -MD -MP -MF .deps/xmlrole.Tpo -c -o xmlrole.o xmlrole.c
mv -f .deps/xmlrole.Tpo .deps/xmlrole.Po
gcc -DHAVE_CONFIG_H -I. -I../../simgear -I../..    -g -O2 -D_REENTRANT -MT xmltok.o -MD -MP -MF .deps/xmltok.Tpo -c -o xmltok.o xmltok.c
mv -f .deps/xmltok.Tpo .deps/xmltok.Po
rm -f libsgxml.a
ar cru libsgxml.a easyxml.o hashtable.o xmlparse.o xmlrole.o xmltok.o 
ranlib libsgxml.a
make[3]: Leaving directory `/home/george/Downloads/SimGear-2.0.0/simgear/xml'
Making all in debug
make[3]: Entering directory `/home/george/Downloads/SimGear-2.0.0/simgear/debug'
g++ -DHAVE_CONFIG_H -I. -I../../simgear -I../..    -g -O2 -D_REENTRANT -MT logstream.o -MD -MP -MF .deps/logstream.Tpo -c -o logstream.o logstream.cxx
mv -f .deps/logstream.Tpo .deps/logstream.Po
rm -f libsgdebug.a
ar cru libsgdebug.a logstream.o 
ranlib libsgdebug.a
make[3]: Leaving directory `/home/george/Downloads/SimGear-2.0.0/simgear/debug'
Making all in misc
make[3]: Entering directory `/home/george/Downloads/SimGear-2.0.0/simgear/misc'
g++ -DHAVE_CONFIG_H -I. -I../../simgear -I../..    -g -O2 -D_REENTRANT -MT sg_path.o -MD -MP -MF .deps/sg_path.Tpo -c -o sg_path.o sg_path.cxx
mv -f .deps/sg_path.Tpo .deps/sg_path.Po
g++ -DHAVE_CONFIG_H -I. -I../../simgear -I../..    -g -O2 -D_REENTRANT -MT sgstream.o -MD -MP -MF .deps/sgstream.Tpo -c -o sgstream.o sgstream.cxx
In file included from sgstream.hxx:40,
                 from sgstream.cxx:28:
../../simgear/misc/zfstream.hxx:32:18: error: zlib.h: No such file or directory
In file included from sgstream.hxx:40,
                 from sgstream.cxx:28:
../../simgear/misc/zfstream.hxx:113: error: &#8216;gzFile&#8217; does not name a type
../../simgear/misc/zfstream.hxx: In member function &#8216;bool gzfilebuf::is_open() const&#8217;:
../../simgear/misc/zfstream.hxx:90: error: &#8216;file&#8217; was not declared in this scope
make[3]: *** [sgstream.o] Error 1
make[3]: Leaving directory `/home/george/Downloads/SimGear-2.0.0/simgear/misc'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/george/Downloads/SimGear-2.0.0/simgear'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/george/Downloads/SimGear-2.0.0/simgear'
make: *** [all-recursive] Error 1


```

Sorry for such a long thing ^.

Thanks for any help.

I'm not that good in Terminal so my problem is probably really stupid.

Thanks.

---

### Post by Sealbhach on 2010-07-04
I use Brisa's [Download and Compile Script]("http://wiki.flightgear.org/index.php/Scripted_Compilation_on_Linux_Debian/Ubuntu"). It worked for me.

However, the link to the script on that page is down at the moment so I put my copy of it on Dropbox [http://dl.dropbox.com/u/1527486/download_and_compile.sh](http://dl.dropbox.com/u/1527486/download_and_compile.sh)

Compiling can be a world of pain but I found this script was easy to use and did everything automatically.

.

---

### Post by Lauxmonster on 2010-07-05
> **Sealbhach said:**
> I use Brisa's [Download and Compile Script]("http://wiki.flightgear.org/index.php/Scripted_Compilation_on_Linux_Debian/Ubuntu"). It worked for me.

However, the link to the script on that page is down at the moment so I put my copy of it on Dropbox [http://dl.dropbox.com/u/1527486/download_and_compile.sh](http://dl.dropbox.com/u/1527486/download_and_compile.sh)

Compiling can be a world of pain but I found this script was easy to use and did everything automatically.

.

Oooo! Thanks alot. I shall see how this works.

---

### Post by hihihi100 on 2010-12-14
I have just downloaded this same Brisa's compilation that downloaded the 7 GBs or so of files, now, to the bugs:

everytime I use it, no matter what plane I choose, i will ALWAYS see another aircraft flying, but the movements of this aircraft are extremely unrealistic: its positions looks like its taking off on a 10 degrees angle, but it only moves vertically, so its like I see an aircraft (I insist its not mine, i can see my cockpit, the controls of MY plane, etc). I can only see its left side, that moves only vertically, till it disappears upwards.

Am I the only one having this problem?

And, Is the FGFS from Brisa's really 2.0? or is it 1.9? I assume u all dont recommend to run the FGFS found in the software center, cause that sure is 1.9 Am i wrong?

cheers

Update: some snapshots

---

