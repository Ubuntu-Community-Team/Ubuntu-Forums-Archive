---
title: "HandBrake 0.7.1 CLI &quot;howto&quot;"
date: 2006-09-11
forum: Desktop Environments
---

### Post by Onos on 2006-09-11
Well... there are a handful of howto's spread around the net for building HandBrake in Ubuntu Linux... but as I have a rather nasty habit of tinkering and (attempting to) tweaking my Linux installs until something breaks horrendously enough for me to need to re-install the OS...

I am hoping to put togther an Ubuntu HOWTO for HandBrake to include some of the "unexpected" cases. Much of it is derived from Mayank Sharma's tutorial at [http://www.linux.com/article.pl?sid=06/04/13/2139238](http://www.linux.com/article.pl?sid=06/04/13/2139238) entitled "CLI Magic: Porting DVDs with HandBrake", but as I ran into a few rough bumps with it...

Here is what I did (again, this is pieced together from a few different HOWTOs) to get it running on my aging machine running Dapper:

-1. Download the source tarball:
```
wget -c http://download.m0k.org/handbrake/HandBrake-0.7.1.tar.gz
```

-2. Install these packages to make the HandBrake happy in its new (Ubuntu/Debian) home:
```
sudo aptitude update
sudo aptitude install jam build-essential nasm libdvdcss2
```

-3. Unzipped/un-tarred it in your home directory:
```
tar xvf HandBrake-0.7.1.tar.gz
```

-4. Rename the HandBrake-0.7.1 directory to HandBrake (trivial, but who really wants to type out all that version info in the path! )
```
mv HandBrake-0.7.1 HandBrake
```

-5. Switch to the HandBrake directory
```
cd HandBrake
```

-6. Configure the source
```
./configure
```

-7. Edit the Jamfile to make Ubuntu/Debian happy: (use your favorite text editor)
```
sudo nano ~./HandBrake/libhb/Jamfile
```

-8. Find the following line: (it should be near the bottom of the file)
```
ObjectCcFlags $(LIBHB_SRC) : -I$(TOP)/contrib/include ; 
```

--8a. Make it look like this:
```
ObjectCcFlags $(LIBHB_SRC) : -I$(TOP)/contrib/include -I$(TOP)/contrib/mpeg4ip/lib/mp4v2 ; 
```

--8b. Save/Write-out of the file...


-9. Jam it all together (requires installation of Jam, see #2 above)
```
jam
```

-10. Finishing up:
```
cp HBTest /usr/local/bin/handbrake
```
This allows you to pass commands to handbrake anywhere in a terminal.


For the record, this rips movies/DVDs to a suitable *.avi or *.mpg slightly faster on my old Compaq Presario running Dapper than the full-on GUI version does in Mac OSX on my fresh-from-the-Apple Store MacBook.


Credits go to [Peter James Bui](http://www.nd.edu/~pbui/index.html), jbird123 from the Ubuntu forums, and Mayank Sharma as mentioned above.

And of course, the coders who put HandBrake together.

 :D

---

### Post by macron1 on 2007-06-30
hi
thanks for the howto. just one question, i ran jam before modifying the jamfile w nano etc. what are some of the possible repercussions? do i need to re-install? thanks

---

### Post by road_rage on 2007-10-28
Just thought I would mention for n00bs like me....
The line that states "sudo nano ~./HandBrake/libhb/Jamfile" did not allow me to edit the file from the current path and instead created a new file. The command "sudo nano ./libhb/Jamfile" worked for me as I was already in my /home/xxxx/HandBrake folder. 

Thank You for this writeup, definitely moved me along to handbraking!

---

