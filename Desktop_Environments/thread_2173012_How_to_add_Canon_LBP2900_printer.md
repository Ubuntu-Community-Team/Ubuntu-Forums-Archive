---
title: "How to add Canon LBP2900 printer?"
date: 2013-09-07
forum: Desktop Environments
---

### Post by giridhar2 on 2013-09-07
I use Ubuntu 13.04 32-bit, on my Intel Core 2 duo Win 7 PC. How can i add my printer : Model - Canon LBP2900 ? I have been searching the internet in vain, for quite sometime. I am a teacher & i need to print my question papers. And, i am tired of Windows 7 & want to give it up slowly...

KIndly help me !! This is urgent !! PLease explain in a way that a person dumb (in Linux, i.e. :) ) would be able to understand. 

Thanks in advance,

 & Regards.

---

### Post by ibjsb4 on 2013-09-07
I do not have any experience with canon, but I did get some forum hits.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Canon+LBP2900&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Canon+LBP2900&sa=Search&cof=FORID:9)

If you need help with trying a fix, please post back :)

---

### Post by giridhar2 on 2013-09-07
Hi, Tx for your quick reply !!

But i dont understand what to do with so many links - honestly !!! Will read up & get back. Guess this will take time. Time to be frustrated !! :mad:

---

### Post by giridhar2 on 2013-09-07
Followed the post #4 of Sivella in this link given by you : [http://ubuntuforums.org/showthread.php?t=1982917](http://ubuntuforums.org/showthread.php?t=1982917). 

Ubuntu has recognized the printer !! But when test print is given, it shows commuunication error - What to do ??

---

### Post by giridhar2 on 2013-09-07
When i give the very fitst command in the post #4 of Sivella, i get this : 

**Command:**
sudo mkdir /var/ccpd

mkdir: cannot create directory &#8216;/var/ccpd&#8217;: File exists

I then continued to give all other commands as given in the post & then ended up with the communication error...

---

### Post by ibjsb4 on 2013-09-07
> **giridhar2 said:**
> When i give the very fitst command in the post #4 of Sivella, i get this : 

**Command:**
sudo mkdir /var/ccpd

mkdir: cannot create directory ‘/var/ccpd’: File exists

Thats ok

1) Create the following directories/file [COLOR=#ff0000]if they are missing[/COLOR]:
 	 		 			 			 				sudo mkdir /var/ccpd
sudo mkfifo /var/ccpd/fifo0
sudo mkdir /var/captmon 			 		
 	
 

So you have either created or verified these files exists.

> I then continued to give all other commands as given in the post & then ended up with the communication error... 		

Did you copy and paste these commands?

---

### Post by pdc on 2013-09-07
there is an ongoing thread on the forum about the LBP 2900

[http://ubuntuforums.org/showthread.php?t=2028339&page=2&highlight=Canon+printer](http://ubuntuforums.org/showthread.php?t=2028339&page=2&highlight=Canon+printer)

but I think if you stick to Sivella's guide

________________________________________________

the most up to date guide from Sivella is this

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

...........if you use Google to translate to your language of choice

Sivella and the Ubuntu guide recommend using 

> ccp://localhost:59787 -E instead of fifo 

so the command to install in CUPS is 

> [COLOR="#EE82EE"]sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 -E[/COLOR]

____________________________________________________________________________________________________________________________________

the problem using Google translate is it adds spaces to command lines for a terminal; where spaces should not be 

___________________________________________________________________________________________________

if I can offer any help I am pleased to do so but you are being guided by another forum member

---

### Post by giridhar2 on 2013-09-08
> **ibjsb4 said:**
> Thats ok

1) Create the following directories/file [COLOR=#ff0000]if they are missing[/COLOR]:
                                                         sudo mkdir /var/ccpd
sudo mkfifo /var/ccpd/fifo0
sudo mkdir /var/captmon                      
     
 

So you have either created or verified these files exists.



Did you copy and paste these commands?

 I copy-pasted as well as typed out the commands.

---

### Post by giridhar2 on 2013-09-08
> **pdc said:**
> there is an ongoing thread on the forum about the LBP 2900

[http://ubuntuforums.org/showthread.php?t=2028339&page=2&highlight=Canon+printer](http://ubuntuforums.org/showthread.php?t=2028339&page=2&highlight=Canon+printer)

but I think if you stick to Sivella's guide

________________________________________________

the most up to date guide from Sivella is this

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

...........if you use Google to translate to your language of choice

Sivella and the Ubuntu guide recommend using 

 instead of fifo 

so the command to install in CUPS is 



____________________________________________________________________________________________________________________________________

the problem using Google translate is it adds spaces to command lines for a terminal; where spaces should not be 

___________________________________________________________________________________________________

if I can offer any help I am pleased to do so but you are being guided by another forum member



PLease, Please offer your help. Formalities only destroy progress. Every minute delayed is hampering my work. You kow, it took  an hour to understand what you meant by google translate adding spaces to terminla commands - holy **** !!! Just now, i have finished step 3.1 

going to step 3.2 - space problem persits here again !

CAn you PLEASE give me ALL THE STEPS  required, here itself ??  I am tired of switching between tabs & doind this ****. I am ****ing tired. I hate Canon !! 
:mad::mad:


Regards

---

### Post by ibjsb4 on 2013-09-08
Sounds like 'pdc' has the expertise that I am lacking, so I hope he will go with this :)

---

### Post by pdc on 2013-09-08
OK:

so if we copy and paste this command into a terminal.......use the mouse and the top line of the terminal; so File is top left corner, then move with mouse along to Edit and down to Paste 

> [COLOR="#FF0000"]dpkg -l | grep Canon[/COLOR]

it will tell us if the CAPT drivers are installed; 

_________________________________________________

if they were, we use this [http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

(the 2 CAPT drivers must be installed in the order: COMMON first and then the other)

_________________________________________________________________________

so for me the command > dpkg -l | grep Canon gives the result > ii  cndrvcups-capt  2.40-1 Canon CAPT Printer Driver for Linux ii  cndrvcups-common 2.40-1 Canon Printer Driver Common Modules Ver.2.40  as I have version 2.4 installed

_____________________________________________________________________

if you have the drivers installed, let's cover the next steps; (if you don't have the drivers installed, tell me and I will cover how to install them)

you have 32bit: great; makes things easier

Install printer in CUPS

> [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 -E[/COLOR]

then register with ccpd daemon

> [COLOR="#FF0000"]sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usb/lp0[/COLOR]

(*this assumes your printer is the only one connected to the computer and is connected via a USB cable so it assumes lp0 as the connection point*)

then start ccpd

> sudo service ccpd start

then check it

> sudo service ccpd status

........you should get something like > Canon Printer Daemon for CUPS: ccpd: 8956 8954

.............now if you open LibreOffice or OpenOffice or Firefox or something.........do you see the LBP2900 mentioned as a printer option? ...................if you can does it print?

______________________________________

If so, 2 more important things to do 

and we will use gedit which is a text editor so you need to check in your Ubuntu software editor it is installed; if not please install it

you will be opening it with sudo rights 
________________________________

> [COLOR="#FF0000"]gksudo gedit /etc/udev/rules.d/85-canon-capt.rules[/COLOR]

this opens a blank page as you are creating new instructions 

COPY and PASTE into it the text below

> KERNEL=="lp*", SUBSYSTEMS=="usb", ACTION=="add", ATTRS{idVendor}=="04a9", RUN+="/etc/init.d/ccpd start"
KERNEL=="lp*", SUBSYSTEMS=="usb", ACTION=="remove", RUN+="/etc/init.d/ccpd stop"

SAVE and then CLOSE

___________________________________

now issue the command

> [COLOR="#FF0000"]gksudo gedit  /lib/udev/rules.d/70-printers.rules[/COLOR]

and this opens gedit again 

this time there is text and you need to change it; if I highlight what you need to add in [COLOR="#0000FF"]BLUE[/COLOR] ? You will be adding hash comments which means the writing is ignored by your system now;

> # Low-level USB device add trigger
[COLOR="#0000FF"]#[/COLOR]ACTION=="add", SUBSYSTEM=="usb", ATTR{bInterfaceClass}=="07", ATTR{bInterfaceSubClass}=="01", TAG+="udev-configure-printer", RUN+="udev-configure-printer add %p"
# usblp device add trigger (needed when usblp is already loaded)
[COLOR="#0000FF"]#[/COLOR]ACTION=="add", KERNEL=="lp*", TAG+="udev-configure-printer", RUN+="udev-configure-printer add %p"

# Low-level USB device remove trigger
[COLOR="#0000FF"]#[/COLOR]ACTION=="remove", SUBSYSTEM=="usb", ENV{ID_USB_INTERFACES}=="*:0701*:*", RUN+="udev-configure-printer remove %p"

..................the result is ALL LINES are marked with hash signs; (I had to do this again to my system last weekend when I installed updates and they changed this file

___________________________________

that should be everything; if you reboot the system, it .......should recognise the printer whenever you turn it on and it should work ........................

---

### Post by giridhar2 on 2013-09-08
I post below Each COmmans typed (according to your instructions) and the respective outputs obtained. Please help.

********************************************************************************************************************************************************************************************************************
Command: 

dpkg -l | grep Canon

Output:

ii  cndrvcups-capt                            2.60-1                                 i386         Canon CAPT Printer Driver for Linux
ii  cndrvcups-common                          2.60-1                                 i386         Canon Printer Driver Common Modules Ver.2.60


Command: 

sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 -E

Output: 

It returned the usual prompt - i.e, Nothing happened.

COmmand: 

sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usb/lp0

Output: 

CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 59787

 Entry Num  : Spooler    : Backend    : FIFO path        : Device Path     : Status 
 ----------------------------------------------------------------------------
     [0]    : LBP3100     :          :                     : /dev/usb/lp0     : invalid Spool Name
     [1]    : LBP2900     : ccp         : //localhost:59787     : /dev/usb/lp0     : Modified


Command: 

sudo service ccpd start 

Output: 

Starting /usr/sbin/ccpd: .


Command: 

sudo service ccpd status 

Output: 

/usr/sbin/ccpd: 12741 12738

********************************************************************************************************************************************************************************************************************

So,it seems i did not get the output that i am supposed to get for the above mentioned command, as mentioned by your good self.

When i open print option in libre office , i do get the LBP2900 printer shown. But nothing prints...

---

### Post by pdc on 2013-09-09
> [COLOR="#EE82EE"]/dev/usb/lp0 : invalid Spool Name[/COLOR]

please tell me how your printer is connected to your computer: the commands I suggested were for a home computer set-up; where there is a stand-alone computer; with an LBP2900 connected via a USB cable directly to the printer, without going through any USB hub or such

---

### Post by giridhar2 on 2013-09-12
Yes, my printer Canon LBP2900 is connected by a USB cable directly to the Windows 7 PC. There is no USB hub. 

I want to tell you that i read through the english translation of the french document - [http://doc.ubuntu-fr.org/tutoriel/in...lote_canon_lbp]("http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp")

 I could not follow it completely. So, i went to the steps mentioned by yourself after the document. COuld that be the reason ? I simply can't follow the document. May be i was irritated by the spaces created by the translated page. IS that my mistake ?

---

### Post by mahesh-2 on 2013-09-24
i am having same issue please help

---

### Post by giridhar2 on 2013-09-28
I was very excited to be using such a fast OS like 13.04. But, the OS keeps resetting my internet connection even when all the settings entered are correct (Windows 7 does not show any problem). Also, i am unable to get 13.04 to print anything on Canon LBP 2900. I appreciate all the help provided by pdc and others, but let me confess that i am not a computer geek .I am a teacher. I would have preferred DIRECT instructions as to how to do it. Clicking a link that is in french, using google translate that inserts unnecessary spaces in command lines - creating problems like this is just too much for me. I would have preferred to use Libre office and print my question papers for my students, directly from ubuntu rather than Windows 7. But if i have to do so much google search and fighting for just a simple thing like attaching a printer & surfing the net( & yet remain unsolved), i shudder to think what would happen if i update the OS. 

As i have decided to go off Windows, my option now is to get a Mac. On my iPad, i have NEVER experienced any problem whatsoever till date (it has been 7 months on iPad now). Till i get a Mac, i would continue Windows 7. I wished Ubuntu had been easy when it comes to basic things like computer accessories. My aim in life is not to be a computer/Linux geek but to use the computer for my work. My valuable time is being lost. It has been more than 2 weeks now and still the printer is unable to print though it is being recognized by Ubuntu.

So, thanks to all. Thank you very much & Regards

---

