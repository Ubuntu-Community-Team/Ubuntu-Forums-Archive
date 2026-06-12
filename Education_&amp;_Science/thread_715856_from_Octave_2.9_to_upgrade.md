---
title: "from Octave 2.9 to upgrade"
date: 2008-03-05
forum: Education &amp; Science
---

### Post by natanel on 2008-03-05
Hi
I am 3 days ubuntu user, quit new 
but every thing is smotter the I thought

I allready instaled octave 2.9 with  QtOctave and Gnuplot

now ,after reading here I understand it will be best uisng

Octave 3.0
with
QtOctave 
and 
EasyPlot1.1

so do I need to uninstal octave 2.9 with  QtOctave and Gnuplot?
or just install the new Octave, QtOctave  and EasyPlot?

how QtOctave will now to use EasyPlot as Gnuplot is allready installed?
were I config it?

is all of you recomand QtOctave then KOctave?

I understand there are more packet to add 
which (doc,liberaries,...) ?
 how?
is it automatic for Octave 3.0?

I read all the information but it is not connecting to one picture, for me

thanks

---

### Post by morticul on 2008-03-05
Here is a thread that tells where to find .deb for installing what you want :
[http://ubuntuforums.org/showthread.php?p=4450724](http://ubuntuforums.org/showthread.php?p=4450724)

By doing it through .deb, your package managers will handle links automatically (I guess). To choose between different installed versions, you can use the update-alternatives command.

If you install it manually by compiling the sources, you'll have to modify the links manually. For example the following command tells you how octave is linked. 

```

ls -l /usr/bin/octave*

```

then you could use the ln command to create new links and rm to remove unwanted links. 

Hope this help...

---

### Post by natanel on 2008-03-06
ok this is what I did

run synaptic and full removed octave 2.9 and  Koctave 
downloaded the deb package of "thisismalhotra"
installed them

and walla

now I don't have any thing

I have this menu icon under programming languages -> gnu Octave when clicking it 
a window is open and close very fast (I can't even see which one)

never found the QtOctave

looked in synaptic and it look like the three deb package are installed

any ideas?

---

### Post by thisismalhotra on 2008-03-06
> **natanel said:**
> ok this is what I did

run synaptic and full removed octave 2.9 and  Koctave 
downloaded the deb package of "thisismalhotra"
installed them

and walla

now I don't have any thing

I have this menu icon under programming languages -> gnu Octave when clicking it 
a window is open and close very fast (I can't even see which one)

never found the QtOctave

looked in synaptic and it look like the three deb package are installed

any ideas?

1. Do following go to terminal and type octave and see if the terminal changes to octave:> .. if yes you have octave installed (octave does not have GUI by itself)

2. For some weired reason qtoctave does not give you a menu entry. I am trying to work it out and improve it but no luck so far. so again in terminal type qtoctave and see if it opens up. If yes, I would set up a launcher on your desktop with command Qtoctave.

3. When in qtoctave go to configuration and tell it to use EasyPlot. Easyplot normally is installed in \usr\local\share (I need to double-check that or do locate easyplot)

Le me know if you are stuck in any of these. We have just got an account from ubuntu and we will try to help out the developers as an octave maintenance team so hopefully in future the deb's would be available through synaptic.

Hope that works !!

---

### Post by ItalOz on 2008-03-06
> **natanel said:**
> never found the QtOctave

in order to have a menu entry for QtOctave I did the following

right click on menu tab and select "edit menus"

chose new Item (for some reason when I do this the new window is hidden behind the principal one so highlight it)

link the new item to your QtOctave file, in my case it was in
/usr/local/bin/qtoctave
I think for you is the same

---

### Post by natanel on 2008-03-06
still a mess

removed octave2.9
tried to install octave3.0 form source--problems

re-instaeld octave2.9 and tried agin to install octave3.0 from source

keep getting
natanel@natanel-desktop:~$ sudo apt-get build-dep octave
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libsuitesparse libsuitesparse-dev
0 upgraded, 2 newly installed, 0 to remove and 18 not upgraded.
53 not fully installed or removed.
Need to get 0B/2142kB of archives.
After unpacking 6291kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 135850 files and directories currently installed.)
Unpacking libsuitesparse (from .../libsuitesparse_3.0.0-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsuitesparse_3.0.0-3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libamd.so.1', which is also in package libumfpack4
Unpacking libsuitesparse-dev (from .../libsuitesparse-dev_3.0.0-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsuitesparse-dev_3.0.0-3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libamd.a', which is also in package libumfpack4-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libsuitesparse_3.0.0-3_i386.deb
 /var/cache/apt/archives/libsuitesparse-dev_3.0.0-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Failed to process build dependencies

also ubuntu is not able to find the ubuntu cd even when it is inserted

any help?

Edit 
after severa instal uninstal I get

natanel@natanel-desktop:~$ sudo apt-get build-dep octave
[sudo] password for natanel:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  texinfo
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/300kB of archives.
After unpacking 2167kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package texinfo.
(Reading database ... 133381 files and directories currently installed.)
Unpacking texinfo (from .../texinfo_4.8.dfsg.1-6_i386.deb) ...
Setting up texinfo (4.8.dfsg.1-6) ...
Running mktexlsr. This may take some time. ... done.

natanel@natanel-desktop:~$ ./config
bash: ./config: No such file or directory
natanel@natanel-desktop:~$ 

how I do config?

---

### Post by thisismalhotra on 2008-03-06
3 things:-

1. Did you use the .deb above link has and see if that build up right??
2. Do you have all the repositories enabled??
3. Go to Software Sources in administration and Uncheck the boc which says CD and source and reload the software sources it will not ask you for CD again.
 Note: Please do all this when you are connected to internet. Uninstall version 2.9 and double click the deb files to install ...

Also r u using Ubuntu 7.10??

If you want to build from source (though .deb is easy/better way to go) use following instructions pls...

[http://ubuntuforums.org/showthread.php?t=680690](http://ubuntuforums.org/showthread.php?t=680690)

---

### Post by natanel on 2008-03-06
did it all

from deb from source

with octave2.9 with out octave2.9

removed CD request

and yes it is 7.10

but with out luck

they should have a package "fix mess of dummy pepole"

any way it midnight here, my baby is going to wake up in few hours and my wife already in deep sleep
I am going to join her and will try to solve it tomorrow

thanks

---

### Post by natanel on 2008-03-07
good morning

I am getting close

10 installing from source - I just don't know from which directory I should run config
if I try to do it from were the console is after downloading, I get, no such file

2) from deb package, manage to run octave but when tring to run qtoctave I am getting qtoctave:
 error while loading shared libraries: libQtXml.so.4: cannot open shared object file: No such file or directory

didn't found any libQt in synaptic

 any help?

---

### Post by thisismalhotra on 2008-03-07
Well you run the ./configure when you are in the directory which has the source you downloaded.

Thats odd with qtoctave, one of the other guys in another thread floating around has the same problem. Since I compiled it from source I think I have all the libraries I needed, I am trying to investigate it but no luck yet. Will let you know if I found a solution...

---

### Post by natanel on 2008-03-07
Hi

I just downloaded almost every thing that have libQt 0,1,2,3,4 from synaptic
and it's working

with easyplot

about ./config, don't have a clue to were the files are downloaded
how I can find it?

I think my ubuntu is a mess after so many install and uninstall
(AWN, screenlet, octave,wine, swcad, eclipse avr32 studio) 
some time it just crash to login screen

so probably I will install every thing from scratch

some octave questions
how I can see which toolbox are installed and which are available to  install?
were and how I can find/install other toolboxes?
is there any equal to maltab guide in octave?

 thanks

---

### Post by thisismalhotra on 2008-03-07
> **natanel said:**
> Hi

I just downloaded almost every thing that have libQt 0,1,2,3,4 from synaptic
and it's working

with easyplot

about ./config, don't have a clue to were the files are downloaded
how I can find it?

some octave questions
how I can see which toolbox are installed and which are available to  install?
were and how I can find/install other toolboxes?
is there any equal to maltab guide in octave?

 thanks

**If you have octave installed I don't see a reason you will run ./configure and not ./config..(You do those if you compile form source)**

Also Octave does not have any toolboxes byt itself... you will need to install octave - forge and that basically are all the toolboxes. The GUI does not work like matl;ab but most of the functions are same.. basically you iwll have some learning to do.

Octave Manual here: -

[http://www.gnu.org/software/octave/docs.html](http://www.gnu.org/software/octave/docs.html)

Octave Wiki (Dont know if it is complete or not) : -

[http://wiki.octave.org/](http://wiki.octave.org/)

Octave-forge(aka toolboxes): -

[http://octave.sourceforge.net/](http://octave.sourceforge.net/)

---

### Post by natanel on 2008-03-07
Ok

so I want to install octave-forge

found there are two ways

one
# adds more functions, better matlab compatibility
sudo apt-get install octave2.9-forge

# full documentation
sudo apt-get install octave2.9-info octave2.9-doc octave2.9-htmldoc
gnuplot-doc

two
and from the web page
"You can find the list of packages by clicking on the Packages link at the top. To install a package, download the package file, and install it from the Octave prompt by typing
pkg install package_file_name.tar.gz
where package_file_name.tar.gz is the name of the file you downloaded. "

now what?
is there a command line to run for downloading and updating all the  octave-forge?
which version?

still counting only 4 days with ubuntu

---

### Post by thisismalhotra on 2008-03-07
Read the fine line dude

"[I]You can find the list of packages by clicking on the Packages link at the top. To install a package, download the package file, and install it from the Octave prompt by typing
pkg install package_file_name.tar.gz
where package_file_name.tar.gz is the name of the file you downloaded. "[/I]

Since you have Octave 3.0 I would download the packages from webpage.

Go to terminal and start octave

then from the octave prompt as it says install the packages...

Hope this works...
How may more days will you count with ubuntu:lolflag:

---

### Post by natanel on 2008-03-07
until I will lose it


first day - :-D

from then going from ](*,) to \\:D/

hope I will not get to that :evil:

many thanks
you are helped me alot

by the way pkg didn't work for me
in octave after downloading pkg
pkg install fixed-0.7.5.tar.gz 
and nothing

---

### Post by thisismalhotra on 2008-03-07
I dont use the toolboxes/packages but I think they install silently and dont tell you 'whoo ye I installed my self' :)

Anyways try using any of the function from that package and see if it installed. I know there is a way to check that in octave just dont know that from top of my head right now...

Have fun and let me know if you get stuck again. 
Just a suggestion, if you whole ubuntu is messed up try a clean install with stuff you know/need now...:KS

---

