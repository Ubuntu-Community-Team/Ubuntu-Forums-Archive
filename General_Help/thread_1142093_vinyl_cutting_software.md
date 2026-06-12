---
title: "vinyl cutting software?"
date: 2009-04-28
forum: General Help
---

### Post by kmrs75 on 2009-04-28
I have been looking for software that will cut vinyl in ubuntu and I cant find anything. I have looked at programs like inkscape but that is for design part of it but there it doesn't support cutting I don't think. 

there has to be some kind of plotting software even if it intended to be used with just an ink plotter I would like to try to use it.

---

### Post by FluffyElmo on 2009-04-28
This may be similar to what you're looking for? I'm not sure if there is much of a gui but it may be a place to start. [http://www.linuxcnc.org/](http://www.linuxcnc.org/)

---

### Post by kmrs75 on 2009-04-28
> **FluffyElmo said:**
> This may be similar to what you're looking for? I'm not sure if there is much of a gui but it may be a place to start. [http://www.linuxcnc.org/](http://www.linuxcnc.org/)

thanks i did go check it out and it doesnt support drawings - but i will send them a message and see what it can do

---

### Post by FluffyElmo on 2009-04-28
It's primarily an interface for various commercial CNC machines and plotters. There has been some effort at making an Inkscape plug-in that generates the necessary code though. If your vinyl cutter is supported it may be a start. 

[http://wiki.linuxcnc.org/cgi-bin/emcinfo.pl?InkscapeHowto](http://wiki.linuxcnc.org/cgi-bin/emcinfo.pl?InkscapeHowto)

---

### Post by kmrs75 on 2009-04-28
> **FluffyElmo said:**
> It's primarily an interface for various commercial CNC machines and plotters. There has been some effort at making an Inkscape plug-in that generates the necessary code though. If your vinyl cutter is supported it may be a start. 

[http://wiki.linuxcnc.org/cgi-bin/emcinfo.pl?InkscapeHowto](http://wiki.linuxcnc.org/cgi-bin/emcinfo.pl?InkscapeHowto)

thanks but most cutters/plotters are not gcode. gcode is a closed loop that gives feedback to a controller so it knows there is on the table. mainly used for larger machines that could have some slip in the drive. if the software says move 300 steps to the right and due to the weight and materal cutting it slips and only moves 280 steps the feedback will indicate where it is and it will keep going till 300 steps is achieved 

open loops cutters/plotters are open loop there is no feed back. the sofware tells it to move 300 steps to the right it assumes that it did move 300 steps. there is no or little drag on these so feed back isnt needed 

im not sure if it will work but it would be worth a try i did see someplace on there websight that it can do open loop but i cant find it now. either way i can try it. 

i was just hoping to find something that was made spacific for plotters and cutters

---

### Post by FluffyElmo on 2009-04-29
So you just need a plotter driver? I think there are some in the add printer dialog. I've also printed graphics in the past by sending straight HPGL to a plotter.

Inkscape will save as .dxf out of the box and a search turned up the following HPGL script for vinyl cutting: [http://freshmeat.net/projects/hpgldistiller/](http://freshmeat.net/projects/hpgldistiller/)

Inkscape is definitely the best vector based graphics program, I'd start there and see what combination of output scripts/filters will generate output your printer can handle.

---

### Post by kmrs75 on 2009-06-10
yes I have been using Inkscape allot lately I use it for all my designing but then I have to take it to windows to cut it and that is a pain. now im trying to get virtual box to work but it will not allow me to open the usb. when I go to my computer C and D drive it there but not USB

---

### Post by FluffyElmo on 2009-06-10
The open source version of VirtualBox doesn't support USB. You have to grab the free version from their website for that. I'm not sure if you have to do other configuration beyond installing it, a quick search of the forums should turn that up.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by kmrs75 on 2009-06-11
thanks i didnt know that i will check it out

---

### Post by kmrs75 on 2009-08-02
well i know its been a while. i did kinda get it to work not really what i was wanting but it does work. 

i started out with virtual box and not sure what was going on with it but windows wouldn't mount the cutter. it was in the list of usb devices but it was greyed out and i couldn't select it. 

i then moved to do searching on finding a way to actually cut from inkscape i have all the information i need (i think) but since i am very new to this i am still learning my way around linux. i don't even know most of the common commands in the terminal. so this has been a huge learning experience for me.

so then i went back to a virtual machine i ended up going with vmware server its open source and it took a little work to get it installed and working but got it done in one day. 

installed the vmware and that was diffrent. then i loaded windows inside and got my drivers and and cutting software loaded and now im cutting 

my next thing to try to figure out is... i would like to be able to design in linux inkscape. then go to my vmware and just do cutting there but i cant copy and paste. i cant have my external hard drive mounted to both operating systems at the same time. i bet there is a way to have them both networked together so i think i might try to play around with that next. any help would be great.

---

### Post by kmrs75 on 2010-02-12
well just wanted to give an update its been a while but with some help from a guy in canada we got it 

he had this project going on for a while it sounds and he has done a great job super work 

now i can cut vinyl in linux -- 

im still very new so i will describe the best i can so forgive me if i mess somethings up 

---- he has a tar.gz that you load it will install all the programs that is needed to make this work 

it will build a cpl of folders some will hold the script 

and one hpgl-hot-folder anything that is copy and pasted or saved to that folder that is a *.pdf or *.ps will then run thru his script and then output to the cutter / plotter 

it works great - there was a few settings that had to be changed 

and after figuring what to do and him changing the script alittle got it to work -- BYE BYE WINDOWS for good now 

i made my first real decal in linux -- but what better that TUX

if anyone needs some help i will be more than happy to pass on as much as much info as  i can -- but he did it all and he gets all the credit not me 
 

[here is the link to get the download]("http://www.securetech-ns.ca/camm-linux.html")

[IMG]http://i684.photobucket.com/albums/vv203/techsx2/TUX.jpg?t=1266025048[/IMG]

---

### Post by cohort on 2010-03-22
That link didn't work for me, so I did a little searching and found [this link for TUX PLOT](http://www.securetech-ns.ca/camm-linux.html)

---

### Post by hansdown on 2010-03-22
There is also EMC2.

[http://www.linuxcnc.org/](http://www.linuxcnc.org/)

---

### Post by kmrs75 on 2010-03-23
> **cohort said:**
> That link didn't work for me, so I did a little searching and found [this link for TUX PLOT](http://www.securetech-ns.ca/camm-linux.html)

thank you for fixing that for me

---

### Post by kmrs75 on 2010-03-23
> **hansdown said:**
> There is also EMC2.

[http://www.linuxcnc.org/](http://www.linuxcnc.org/)

i have looked into that a few times that is diffrent than vinyl cutting 

that is for mills - cnc routers - anything that uses Gcode 

vinyl cutters and plotters use HPGL it could work if you converted hpgl to gcode 

anyone else using this TUX PLOT

---

### Post by frmdstryr on 2010-04-08
I wrote a plugin for inkscape, get it here..  [http://www.inkscapeforum.com/viewtopic.php?f=31&t=4987&e=0](http://www.inkscapeforum.com/viewtopic.php?f=31&t=4987&e=0)

Let me know if it works or if you have some problems, I can try to fix them.

---

### Post by kmrs75 on 2010-04-09
> **frmdstryr said:**
> I wrote a plugin for inkscape, get it here..  [http://www.inkscapeforum.com/viewtopic.php?f=31&t=4987&e=0](http://www.inkscapeforum.com/viewtopic.php?f=31&t=4987&e=0)

Let me know if it works or if you have some problems, I can try to fix them.

i will try it out later today or this weekend - i did load it and it looks cool 

have you tried tuxplot 

what do you use it with what kind of cutter 

we have a graphtec

---

### Post by kmrs75 on 2010-04-09
setting up a vinyl cutter, engraver, plotter in linux

[http://www.youtube.com/watch?v=Seaje_YJ5sU]("http://www.youtube.com/watch?v=Seaje_YJ5sU")

setting up TUX PLOT linux software for hpgl code 

[http://www.youtube.com/watch?v=1fRE0n5Kj5Y]("http://www.youtube.com/watch?v=1fRE0n5Kj5Y")

how to cut from linux using inkscape 

[http://www.youtube.com/watch?v=yjCcadSkSj0]("http://www.youtube.com/watch?v=yjCcadSkSj0")

---

### Post by kmrs75 on 2010-04-10
here are some links for vinyl cutters in linux 

it is also good for engravers and plotters almost anything that takes HPGL code

---

### Post by PowerRanger on 2011-06-04
I had Inkscape/ TuxPlot working ~ a month or so ago, then I think a new cups came out which I updated to without having the plotter plugged in.  Then I had to reinstall my cutter in printer conf. and can't get it to work.  I had this same problem when I first installed it, but I don't remember the fix.  I'm almost positive it is permissions related, but am at a loss for how to figure out where this is now failing.  

I'm mad at myself for forgetting, this was only a couple months ago. Arghhh- help please.  

I can drop a .ps into hpgl-hot and temp.plot is created, but when and how does that get sent to the cutter?  I know it is when I click 'ok' in TuxPlot, but which script or what part of this process is failing?  What is happening or not happening?  I can also send to the cutter from a regular print dialog ( file | print).  It will get a hpgl error on the cutter, but at least it is talking to the device. 

TIA

---

### Post by PowerRanger on 2011-06-04
> **PowerRanger said:**
> I had Inkscape/ TuxPlot working ~ a month or so ago, then I think a new cups came out which I updated to without having the plotter plugged in.  Then I had to reinstall my cutter in printer conf. and can't get it to work.  I had this same problem when I first installed it, but I don't remember the fix.  I'm almost positive it is permissions related, but am at a loss for how to figure out where this is now failing.  

I'm mad at myself for forgetting, this was only a couple months ago. Arghhh- help please.  

I can drop a .ps into hpgl-hot and temp.plot is created, but when and how does that get sent to the cutter?  I know it is when I click 'ok' in TuxPlot, but which script or what part of this process is failing?  What is happening or not happening?  I can also send to the cutter from a regular print dialog ( file | print).  It will get a hpgl error on the cutter, but at least it is talking to the device. 

TIA


Alright, I've got it going again- I called launch.sh from /$HOME/bin and it error-ed on the printer name.  I got rid of everything in the printer name except for graphtec and its working again. :P

---

