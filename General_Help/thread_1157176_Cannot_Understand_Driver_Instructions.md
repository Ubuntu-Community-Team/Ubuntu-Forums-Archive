---
title: "Cannot Understand Driver Instructions"
date: 2009-05-12
forum: General Help
---

### Post by italianoman421 on 2009-05-12
I need to install the fan driver for Ubutntu that increases how often it runs. I found the driver at [http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/)
downloaded it and extracted it. This is where I became lost.
The instructions say the following and I do not know how to follow them. Any help is appreciated for how to do this.

Download/Build
dellfand is only available as a source tarball, since the static build would quickly overwhelm my bandwidth quota.

    dellfand-0.9.tar.bz2 

Extract with

    tar xvf dellfand-0.9.tar.bz2 

Build with

    cd dellfand-0.9; make 

CommandLine Usage
Without arguments, the daemon will print the fan status once and exit.

Normal usage is:

    dellfand mode sleep-seconds off low high 

You must run as root. All arguments are mandatory.

    * mode
      0 - run in the foreground, print stats periodically
      1 - run in the background as daemon, no output
    * sleep-seconds
      dellfand will check the CPU temperature with this interval and adjust the fan speed according to the last 3 arguments
    * off
      when the fan is on, turn it off when the temperature has dropped to this level
    * low
      turn the fan to low speed when it reaches this temperature
    * high
      turn the fan to high speed when it reaches this temperature 

Info Line
dellfand displays output like this:

    Fan 0 Status 1->0 Speed 77640 CPU Temp 29C 

Meaning fan 0 is running at 77640rpm, the temperature is 29 degrees celcius and the fan status has just been changed from 1 to 0 (i.e. the fan is moving from low speed to off, so the speed will shortly be 0).

---

### Post by BslBryan on 2009-05-12
Hello, italianoman421. :-)

I'm a little confused, I'm afraid.  Your commands look good, and it looks like it *did* install correctly.

I must be misunderstanding something here.  Would it be at all possible to explain your problem a little differently?

---

### Post by italianoman421 on 2009-05-12
All I did was download the file and extract it. I did not know what "build" and "make" mean. I do not know which commands to issue. What you are reading is not something I copied from the termminal but the instructions from the website I got the program from.

What you see in bold are the instructions from the websitethat I do not understand how to follow, not my issued commands. 

[B]Download/Build
dellfand is only available as a source tarball, since the static build would quickly overwhelm my bandwidth quota.

dellfand-0.9.tar.bz2

Extract with

tar xvf dellfand-0.9.tar.bz2

Build with

cd dellfand-0.9; make

CommandLine Usage
Without arguments, the daemon will print the fan status once and exit.

Normal usage is:

dellfand mode sleep-seconds off low high

You must run as root. All arguments are mandatory.

* mode
0 - run in the foreground, print stats periodically
1 - run in the background as daemon, no output
* sleep-seconds
dellfand will check the CPU temperature with this interval and adjust the fan speed according to the last 3 arguments
* off
when the fan is on, turn it off when the temperature has dropped to this level
* low
turn the fan to low speed when it reaches this temperature
* high
turn the fan to high speed when it reaches this temperature

Info Line
dellfand displays output like this:

Fan 0 Status 1->0 Speed 77640 CPU Temp 29C

Meaning fan 0 is running at 77640rpm, the temperature is 29 degrees celcius and the fan status has just been changed from 1 to 0 (i.e. the fan is moving from low speed to off, so the speed will shortly be 0).[/B]

---

### Post by italianoman421 on 2009-05-12
Just to clear it up again, I have not installed or issued any commands. I simply downloaded the file and extracted it to desktop. It not installed because I do not understand the build and make commands or how to properly follow the instructions.

---

### Post by robertltux on 2009-05-12
okay lets do a bit of rewriting here

the original
Extract with

tar xvf dellfand-0.9.tar.bz2

Build with

cd dellfand-0.9; make
and now a bit of rewriting to clear this up a bit

tar -xvf dellfand-0.9.tar.bz2

this will create a folder named dellfand-0.9 in the same directory where
you have the file

then move into the created directory (this is the cd dellfand-0.9 bit)
and type
make [enter key goes here]
while in that directory you should be seeing a bunch of stuff fly by as your applet gets built

note installing the kernel-source package before you even try using make would be a good idea (since you have to ap-get a very long list of stuff otherwise)

---

### Post by italianoman421 on 2009-05-13
Sorry, but I am really new to Linux, so I am confused about the process here, and I would need this explained out almost step my step. 

So far I have downloaded and extracted, creating a file for the program on the desktop. That is all I have done. I do not understand what it means to "build". I assume you type 
"cd dellfand-0.9; make" into the terminal ~ is that right? but I am lost after that.

The whole instruction part of the site [http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/) is confusing for me as such a new user.

---

