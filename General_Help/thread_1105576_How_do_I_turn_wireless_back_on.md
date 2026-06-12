---
title: "How do I turn wireless back on?"
date: 2009-03-24
forum: General Help
---

### Post by ASL4U on 2009-03-24
Frustrated to no end.. and so OVER surfing the help files to find no answers.

I was working on a nice Ubuntu system.. everything worked... 
andthen I was trying to figure out how to install the driver for a new Pinnacle PCTV HD Pro stick.. so I could watch TV on my computer...

I have been working on it for 5 1/2 hours... THOUGHT maybe I had gotten something done... but had to reboot..
upon reboot -not only does the PCTV not work -
but my wireles network is Locked... It knows there is a wireless system there - but it is now listed as hidden and if I click connect - it immediately tells me that the wireless system is disconnected... I surfed help again for an hour or so - and found a page that says: check to see if the device is on and when I go there is says check for a connection to the router.. and when I go there it says - check to se eif the device is on..

how?
how do I check to see if its on?.. it WAS on - it has been on .. I did not turn it off.
Iwconfig tells me I have no wireless extentions  for lo, eth0, wmmaster0
it knows about everthing else - 
it just will not connect...
and there are no instructions for how to make it connect...

and right now - I could cry.
because now - I get to sit here and wait until someone comes along to tell me I didnt' give youall enough information.. or that I didn't look in the right place ..
HOW DO I TURN IT BACK ON?
simple question..

thank you for listening...

---

### Post by Ericyzfr1 on 2009-03-24
Edit your connection, delete it and then reconnect.

---

### Post by aesis05401 on 2009-03-24
When you say that you are searching help files.. does that mean using a search engine or reading documentation that accompanies the device/software?

I plugged 'PCTV Ubuntu' into Google and found a number of hits related to installing PCTV HD cards on Ubuntu.  

I don't have one of these devices to test, but here is a hit from within the top five hits Google returned:
[http://www.zimbio.com/Ubuntu+Linux/articles/151/Ubuntu+And+Pinnacle+PCTV+HD]("http://www.zimbio.com/Ubuntu+Linux/articles/151/Ubuntu+And+Pinnacle+PCTV+HD"), and it looks pretty straight forward.  

As for the networking issue, have you modified your interfaces file manually?  I have seen weird unavailable states after manually modifying my interfaces file and then attempting to access network device properties through gnome NM.

---

### Post by philinux on 2009-03-24
> **ASL4U said:**
> Frustrated to no end.. and so OVER surfing the help files to find no answers.

I was working on a nice Ubuntu system.. everything worked... 
andthen I was trying to figure out how to install the driver for a new Pinnacle PCTV HD Pro stick.. so I could watch TV on my computer...

I have been working on it for 5 1/2 hours... THOUGHT maybe I had gotten something done... but had to reboot..
upon reboot -not only does the PCTV not work -
but my wireles network is Locked... It knows there is a wireless system there - but it is now listed as hidden and if I click connect - it immediately tells me that the wireless system is disconnected... I surfed help again for an hour or so - and found a page that says: check to see if the device is on and when I go there is says check for a connection to the router.. and when I go there it says - check to se eif the device is on..

how?
how do I check to see if its on?.. it WAS on - it has been on .. I did not turn it off.
Iwconfig tells me I have no wireless extentions  for lo, eth0, wmmaster0
it knows about everthing else - 
it just will not connect...
and there are no instructions for how to make it connect...

and right now - I could cry.
because now - I get to sit here and wait until someone comes along to tell me I didnt' give youall enough information.. or that I didn't look in the right place ..
HOW DO I TURN IT BACK ON?
simple question..

thank you for listening...

Exactly what commands have you use in the terminal?

---

### Post by ASL4U on 2009-03-25
If anybody ever questions whether I'm a geek or not - they need to see me at 4:30am - still trying.

@ericyzfr1 - I will try this first. I'm just always a bit reticent to delete something that works (has worked)

@aesis05401 - when I say I have searched, I mean I have done not less than 3 or 4 google searches with Ubuntu and PCTV - or pinnacle PCTV HD Pro or some version of the two, switching and changing " " so that I might get a new shuffle of the results.. and that after having read 30 or 40 web pages (yes - even those dated 2005, 2006 2007...) and so finally "duh" adding "2009" to the search.. 
I have found many "helpful" descriptions that almost ALL end up with -
dang - it wont work... or Wow - this is great! (but no clear way to do, whatever it was they did.. to make it work.)

@philinux - first... I am a DOS baby... so I'm not completely stupid about the command line... although - I am very new to linux...so indeed - I am fumbling around - trying to figure out commands that I know how to do in Dos - so surely I should be able to do in Ubuntu... 
I do not know where to put directories... and I am not comfortable with the concept of being locked out of my system files... (although I have not turned off that protection...) so in  many cases - my hands are tied when trying to do ANYthing at the terminal.

I am following:
[http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)
and
[http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/pctv_hybrid_pro_stick&sa=X&oi=translate&resnum=7&ct=result&prev=/search%3Fq%3Dubuntu%2Bpinnacle%2Bpctv%2Bhybrid%2Binstallation%26hl%3Den%26lr%3D%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-GB:official%26hs%3DIf0](http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/pctv_hybrid_pro_stick&sa=X&oi=translate&resnum=7&ct=result&prev=/search%3Fq%3Dubuntu%2Bpinnacle%2Bpctv%2Bhybrid%2Binstallation%26hl%3Den%26lr%3D%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-GB:official%26hs%3DIf0)

they are both doing about the same thing... but one is more clear than the other in various places... I follow the one, step by step until either I cant figure out what its telling me to do or I cannot make it do it... at which point I go check out the other and see how they described the doing.

so I have installed a bunch of files (which I will go about uninstalling this morning to see if I can wake up my network... it is asleep (quote from Ubuntu: wmaster0: unknown hardware address type 801 - no working leases in persistent databse - sleeping.)...

I did not mess with any config files... but I did try to make this driver thing...
when I tried to run: sudo apt-get install linux-headers-`uname-r` 
I got an error (multiple times)... about no linux headers found so this step has been skipped... I dont know what uname-r is.. and I'm confused as to whether the ' ' mean I should be putting something else in there - is that user name?... or just say 'uname-r'... and believe someone knows more than I do (which is what I've done)...

at this point - I have stuff in my computer - that I dont know and I dont know where it is (and I really dislike that feeling... ) I do not quite know how to get it all out - so I can start over... and perhaps get it right this time...
but one thing is for sure... - I cant do anything with apt-get - until my network is back up...

and damn.. my computer was running so nicely before I got ambitious.

thanks for listening.. I'm going now to increase my stress level to a far more uncomforatble state - and see if I can undo - what ever it is that I've done...

---

### Post by ASL4U on 2009-03-25
Good morning - again.
it is now 9:41 - and I have network!

apparently I had inadvertently moved my network drivers from one directory - into another... I realized this on a hunch.. nothing more.

I look forward to the day I know where linux keeps stuff.. so I can know where its best to PUT stuff... directions that just say: make a new directory in a convenient place... dont help much - because I dont know if the directory is a temporary one or the permanent one... that will have references to it and once its there it cannot be moved.

still do not have PCTV card working.. but I have wireless - so I'm much relieved.

whole ton of hours that could have (and should have) been spent doing other things...

this is the only part of Ubuntu that I dont like... the number of helpless, intense, mentally challenging hours it takes to try to figure out how to resolve a problem. 

sigh
thanks for listening again - 
and for all your questions - they actually gave me a good place to start again when I did not know what else to look at...

---

### Post by aesis05401 on 2009-03-25
Hey, running out the door, but saw your uname -r comment re: linux headers above. 

uname = print system information
uname -r = print kernel release information

Type 'man uname' for more info, but first off, just type uname -r at a terminal, now take that info and manually append it to the end of the linux-header file you are trying to install.

When you are trying to grab the linux headers you need to specify the kernel release for which you want headers - hence the 'uname -r'/kernel release at the end of the header file name to make sure the one you are downloading matches your install.

Gotta run.

---

