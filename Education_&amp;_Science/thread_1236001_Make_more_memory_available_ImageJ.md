---
title: "Make more memory available ImageJ"
date: 2009-08-09
forum: Education &amp; Science
---

### Post by samden on 2009-08-09
I need to make more memory available to ImageJ, and this should be a very easy thing to do according to the online documentation - all I need to do is tweak the "run" script:
[http://rsb.info.nih.gov/ij/docs/install/linux.html]("http://rsb.info.nih.gov/ij/docs/install/linux.html")

But where is this "run" script? 

It is apparently located in the "ImageJ folder" - but what folder is that? I have "imagej" folders in:
/usr/share/imagej   - contains folders "luts", "macros" and "plugins"
/usr/share/doc/imagej - contains documentation files only (as expected!)

Sometimes the simplest things are the most frustrating... :)

EDIT:
By "run" script the documentation may be referring to /usr/bin/imagej. This file contains:
```
############ DEFAULT MEMORY SETTINGS  #########################

declare -i default_mem=768
declare -i min_mem=32
declare -i max_32bit=1800 # empirical
declare -i max_64bit=17000000000 # conservative

############ MEMORY ALLOCATION #########################

OS=$(uname)
processor=$(uname -m) # -p doesn't work on debian/ubuntu
declare -i mem
declare -i max_mem
declare -i free_mem

java_home="${java_home:-$JAVA_HOME}"

if [[ "$OS" == 'SunOS' ]] ; then
    java_arch='-d64'
	JAVA_HOME="${java_home_SunOS:-$java_home}"	
	max_mem=`vmstat | awk 'BEGIN{maxMem='$max_64bit'} NR == 3 {fmem=int($5 / 1024); if (fmem < maxMem) {print fmem} else {print maxMem}}'`
	free_mem="max_mem"
	mem=${free_mem}/2
	if (( $mem > $default_mem || $mem < $min_mem )) ; then mem=$default_mem ; fi
elif [[ "$OS" == 'Linux' ]] ; then
	if [[ "$processor" == 'x86_64' ]] ; then
    	java_arch='-d64'
        JAVA_HOME="${java_home_Linux_x86_64:-$java_home}"
    	max_mem=`free | awk -v maxMem=$max_64bit 'NR == 2 {fmem=int($2 / 1024); if (fmem < maxMem) {print fmem} else {print maxMem}}'`
		free_mem=`free | awk -v maxMem=$max_64bit 'NR == 3 {fmem=int($4 / 1024); if (fmem < maxMem) {print fmem} else {print maxMem}}'`
		mem=${free_mem}/3*2
		if (( $mem > $default_mem || $mem < $min_mem )) ; then mem=$default_mem ; fi
	else
		java_arch='-d32'
    	JAVA_HOME="${java_home_Linux:-$java_home}"
    	max_mem=`free | awk -v maxMem=$max_32bit 'NR == 2 {fmem=int($2 / 1024); if (fmem < maxMem) {print fmem} else {print maxMem}}'`
		free_mem=`free | awk -v maxMem=$max_32bit 'NR == 3 {fmem=int($4 / 1024); if (fmem < maxMem) {print fmem} else {print maxMem}}'`
		mem=${free_mem}/3*2
		if (( $mem > $default_mem || $mem < $min_mem )) ; then mem=$default_mem ; fi	
	fi
fi

```
Although the "default" memory value is set at 768MB, on my computer with 1GB of RAM (running fluxbox so most of this is free) ImageJ is only allocated 266MB. I think I need to get this up to 500MB or so. I am running 32 bit Ubuntu.

- Should I be editing this "imagej" script, or another file?
- How should I edit it?

---

### Post by hubie on 2009-08-10
How do you normally run ImageJ?  From the command line, or from an application launcher?  If you run it from the command line, say by typing "imagej" at the prompt, try:
```
$whereis imagej
```
and it will tell you what it is calling, i.e., where your run file is.

If you are using an application launcher, you can right-click on it, go to Properties, and it will show you where the run file is.

I suspect either case will turn up the file you posted, which would be the one you'd want to edit (using a regular text editor).  What you posted is just some fancy shell scripting that tries to figure out how much memory you have free and it sets the ImageJ memory to 2/3rds that.

There are a couple of things you can try.  You can write your own run script, which is really just putting together a one-line command line to send that has the path to the appropriate java installation as well as the memory you want to use, or you can manage the memory from within ImageJ.

To write your own run script, look at the example "Creating a Gnome (Ubuntu) Launcher" from [this page]("http://rsbweb.nih.gov/ij/docs/install/linux.html").  Before going through all the steps they show you for creating the launcher, you can test the command out from a command line to see if it works.

To manage memory from within ImageJ, go to Edit->Options->Memory&Threads and see what happens when you change the assigned memory to what you want.  Before doing that, you might want to run the "free" command from the command line to see how much free memory you have.  You can also see what the memory load is while running ImageJ by going to Plugins->Utilities->MonitorMemory

On top of all of that, don't forget that Virtual Stacks are your friend.  They don't work for everything, but they are very handy where they can be used.

---

### Post by samden on 2009-08-10
Thanks hubie for the very detailed reply. I either start from the command line or by right-clicking a file and selecting "open with ImageJ". 

I have just discovered that although my machine has 1GB of RAM a good chunk of this appears to be stolen for graphics, leaving me only 766MB to play with. Bother. Doesn't look like I'll be able to increase it as much as I was hoping. 

This time when I started it I had 301 MB (from Help > About ImageJ). I should be able to squeeze this up to 500 or more if I aren't running anything else.

Edit > Options > Memory & Threads will not allow me to increase the memory, I get an error with a reference to the ImageJ documentation on the internet.

I'll have a play with scripts and report back.

---

### Post by samden on 2009-08-10
I have adjusted /usr/bin/imagej (the fourth-to-last line in the above quote) from:
```
mem=${free_mem}/3*2
```
to:
```
mem=${free_mem}/6*5
```
giving myself 5/6 of the available memory instead of 2/3 of it. With this I can get 486MB of memory if I start ImageJ with no other programs open. This will hopefully be adequate, if not I can adjust it to use all available memory.

Thanks heaps for your help hubie. I am learning a lot!

---

### Post by hubie on 2009-08-11
You are quite welcome.  ImageJ is a very handy program; I use it a lot and I'm not even in the biology community from which it came.

Be careful trying to squeeze too much memory out of the program.  If you go too far and take up too much, then you'll take a performance hit as your system starts to do a bunch of page swapping.  If you find that memory limits are affecting you, try using virtual stacks (if you open a bunch of images at once), or write your own macros to only work on the images you need at that moment.  Macro writing is very easy to pick up because ImageJ has a macro recorder built in (if you want to do that, you'll find [this document]("http://rsbweb.nih.gov/ij/docs/ImageJMacroLanguage.pdf") very handy).  

I really want to write my own plugins, but I haven't gotten around to figuring out how to do that yet.

---

### Post by samden on 2009-08-11
Virtual stacks aren't an option for me in this case, I'm trying to work with one large image rather than a number of small ones. But I'll remember them for future.

I will be needing to write macros soon once I get my analysis fine-tuned, thanks heaps for that document, it will be a great help.

I had a more ImageJ specific question about an analysis (rather than a Linux question like this one), sent it to the [mailing list]("http://n2.nabble.com/ImageJ-f588099.html"), and within 12 hours had two different workarounds suggested and a request for a sample image so the program could be improved! I am very impressed with the active and helpful community. 

You'd get the workarounds from a forum on proprietory software, but you would be pushing your luck to have someone offer to improve the software itself. The FOSS community is awesome.

---

### Post by hubie on 2009-08-12
> **samden said:**
> You'd get the workarounds from a forum on proprietory software, but you would be pushing your luck to have someone offer to improve the software itself. The FOSS community is awesome.

[As Harry Tuttle said]("http://www.imdb.com/video/screenplay/vi4256891161/"), we're all in this togther! :)

---

### Post by bjordan555 on 2009-10-25
It's also worth noting that from the shell, you can execute "imagej" with the "-x <MB>" option, to specify the amount of available memory.  For my machine with 4 GB ram, the default 768 MB is fine, but for certain jobs, specifying the memory is useful.

---

### Post by nutsy.ben on 2011-01-12
in /usr/bin/imagej

edit the default_mem in the variable declaration.
Then you need to play a bit with the code in max memory allocation. You have 'if'  section, the first one is for sun environment, the second for linux 64 the third for Linux 32 bits.

Edit the max_mem and free_mem.

And hop you can play in my case up to 12 Gb of memory.

Cheers

---

