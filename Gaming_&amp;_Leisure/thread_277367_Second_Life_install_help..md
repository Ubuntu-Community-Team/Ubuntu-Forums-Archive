---
title: "Second Life install help."
date: 2006-10-14
forum: Gaming &amp; Leisure
---

### Post by brklaus on 2006-10-14
Just downloaded the Second Life Alpha client for Linux.  I need a bit of a How-to for installing, i dont see any documentation on how to do that either in the SL package or on the SL site.

Any help would be great.
--B

---

### Post by meng on 2006-10-14
Best guess:
In the terminal, go to the directory where you downloaded the file (.tar.bz2) and:
tar jxvf SecondLife(etc).tar.bz2
cd SecondLife(etc)
./configure
make
sudo make install
(enter your user password here)

---

### Post by AndEat on 2006-10-16
I had little trouble getting it running --

 1. unpack 

    tar -xjf /SecondLife.filename

 2. cd <tab> SecondLife

 3. ./secondlife

 4. Wait for error messages, scratch head 

 5. Hit the SL Linux forums

 6. I had to edit xorg.conf a bit; but your results and mileage may vary

---

### Post by KhaaL on 2006-10-16
> **brklaus said:**
> Just downloaded the Second Life Alpha client for Linux.  I need a bit of a How-to for installing, i dont see any documentation on how to do that either in the SL package or on the SL site.

Any help would be great.
--B

meng's solution does not apply for SL's alpha client. What you need to do is download it, tar xjvf it, enter the directory, and then enter ./secondlife to launch the client.

You may have to mute audio in order to play, depending on what problems you run into. anyway, SL's linux gurus are VERY helpful, so head there if you need help :)

---

### Post by Robertjm on 2006-10-22
To launch you will apparently need to use ./secondlife.sh --aditi

aditi is the name of the preview grid they currently have open. I tried it this morning, but it tells me to check my username/pwd to make sure its correct, which it is. 

My guess is that since I just signed up this morning, I can't get into the preview grid [-( 

Anyone notice how soon after they signed up there were able to log into the preview grid?

Robert

---

### Post by williamts99 on 2006-10-23
I downloaded SecondLife_i686_1_12_2_9.tar.bz2 from the site, double clicked on the file, extracted to desktop, opened folder double clicked on file 'secondlife' and click on run, worked perfectly.

---

### Post by Robertjm on 2006-10-23
So is 1.12.2.9 NEWER software than 1.12.3.2???

Robert

> **williamts99 said:**
> I downloaded SecondLife_i686_1_12_2_9.tar.bz2 from the site, double clicked on the file, extracted to desktop, opened folder double clicked on file 'secondlife' and click on run, worked perfectly.

---

### Post by Somniis on 2006-10-24
I downloaded this and did exactly what williamts99 did.  Just right-click the 'secondlife' executable and Open it.  It should work flawlessly. :)

---

### Post by Robertjm on 2006-10-24
Still having issues so I went to the Beta Grid website. They updated it with info on the user list. Apparently, they only have profiles on it from October 16, or earlier, so that explains why I don't exist on it.

Here's the exact text:

"The beta test grid's database snapshot is from October 16, 2006. If your account is newer than that date, or your password has changed since that date, you will be unable to access the beta test grid."

Guess I'll have to wait for the next snapshot to be done. :-(

Robert

> **Somniis said:**
> I downloaded this and did exactly what williamts99 did.  Just right-click the 'secondlife' executable and Open it.  It should work flawlessly. :)

---

### Post by Somniis on 2006-10-24
> **Robertjm said:**
> Still having issues so I went to the Beta Grid website. They updated it with info on the user list. Apparently, they only have profiles on it from October 16, or earlier, so that explains why I don't exist on it.

I think I read that the Linux client will only run on the main grid.  So, yeah, it won't work on the beta.  (if I did indeed read that)

My computer doesn't run SL very well, so I doubt I'll be playing it.  It looks fun though. :)

---

### Post by shaviro on 2006-10-25
I haven't been able to get it to run. 

I get a "Window Creation Error."

The relevant bits of the output in Terminal seem to be the following:

2006-10-26T03:39:36Z INFO: createContext: window creation failure. SDL: Couldn't find matching GLX visual

and later:

2006-10-26T03:39:40Z WARNING: LLWindowManager::create() : Error creating window.2006-10-26T03:39:40Z WARNING: Unable to create window, be sure screen is set at 32-bit color in Control Panels->Display->Settings

I am pretty sure my screen is set to 32-bit color already; in any case, Control Panels etc refers to Windows, I think, not to Ubuntu.

Any suggestions on what I need to do? Change xorg.conf in some way?

thanks

---

### Post by Somniis on 2006-10-26
If you set the depth to 24 when configuring X, then yes, it should be 32 already.  And yeah, the Control Panel is for Windows. :)

---

### Post by shaviro on 2006-11-03
From what I have been able to gather from the Second Life alpha-for-Linux forums, the real problem behind the "Window Creation Error" is that I need "direct rendering" for the program to work. But all I seem to have is indirect rendering:

shaviro@Naufana:~/SecondLife_i686_1_12_3_6$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

But everything I can find about turning on direct rendering assumes the presence of Nvidia drivers, which apparently I don't have.

Any suggestions on how to turn on direct rendering with Mesa (if that is what I have)?

---

### Post by hikaricore on 2006-11-06
> This is an ALPHA release of the Second Life linux client.
Thank you for testing!
You can visit the Linux Client Alpha Testers forum at:
[http://forums.secondlife.com/forumdisplay.php?forumid=263](http://forums.secondlife.com/forumdisplay.php?forumid=263)


...

You must log in to view the Second Life forums.

If you recieve this error after successfully logging in to other parts of the Second Life website, **please make sure that**:

**    * You have logged in to Second Life at least once with your account.**


ROFLMFAO

Beautiful they created a fubar situation for anyone who's never logged into the game and can't launch it.  LOL  guess I can login to the game via vmware and watch my system nearly die (if i'm even that lucky)... then and only after this does or doesn't actually occur I can check the support forums.  Brilliant!  If only ubuntu had been setup this way ;)  j/k

---

### Post by PriceChild on 2006-11-06
> **shaviro said:**
> Any suggestions on how to turn on direct rendering with Mesa (if that is what I have)?What video card have you got? Pm me and i'll find you a link to install "real" drivers for it.

---

### Post by redgum on 2006-11-18
This worked for me... 

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

I still had default drivers in - once I loaded up the right ones, it all came to life!

---

### Post by sebi k on 2007-03-02
Just for those trying to get the client run on a 64bit Ubuntu, works fine for Feisty
[http://srv4nt.net/blog/second-life/second-life-on-ubuntu-edgy-64-bit/](http://srv4nt.net/blog/second-life/second-life-on-ubuntu-edgy-64-bit/)

---

### Post by sebi k on 2007-03-02
Said to eraly that it works.
The client starts but i can't connect.
It sais
> Unable to connect to Second Life
DNS could not resolve the host name.
Please verify blubb..
And i can't go to the Support Forum, as mentioned above, because i never logged in.:( 
I quote the relevant console output
> 2007-03-02T14:17:41Z INFO: LLUserAuth::authenticate: uri=https://login.agni.lindenlab.com/cgi-bin/login.cgi
2007-03-02T14:17:41Z WARNING: Packet  from invalid circuit 66.150.244.151:12036
[B]2007-03-02T14:17:41Z ALERT: LLXMLRPCTransaction CURL error 6: Couldn't resolve host 'login.agni.lindenlab.com'
2007-03-02T14:17:41Z ALERT: LLXMLRPCTransaction request URI: [https://login.agni.lindenlab.com/cgi-bin/login.cgi](https://login.agni.lindenlab.com/cgi-bin/login.cgi)[/B]
2007-03-02T14:17:41Z INFO: Processed response: 6
2007-03-02T14:17:41Z WARNING: Alert: [ErrorMessage] 
2007-03-02T14:17:41Z WARNING: Alert: Unable to connect to Second Life.
2007-03-02T14:17:41Z DNS could not resolve the host name.

Any ideas, maybe another server to connect? But where to change??

Thanks :)

---

### Post by wieman01 on 2007-03-02
> **sebi k said:**
> Said to eraly that it works.
The client starts but i can't connect.
It sais

And i can't go to the Support Forum, as mentioned above, because i never logged in.:( 
I quote the relevant console output

Any ideas, maybe another server to connect? But where to change??

Thanks :)
I had to disable my firewall using Firestarter in order to establish a conection.

---

### Post by sebi k on 2007-03-02
Don't know if im running a firewall :confused: 

Where to look?

---

### Post by wieman01 on 2007-03-02
> **sebi k said:**
> Don't know if im running a firewall :confused: 

Where to look?
If you don't know anything, you should be ok. You have to configure a firewall manually in the first place as it is down by default. 

But you can connect to the internet with no problem?

---

### Post by sebi k on 2007-03-02
ok then i have none..

yes, im online just while writing this.
also email and gaim are working fine.

---

### Post by sebi k on 2007-03-02
Maybe someone could look in the SL forums, because i can't get in there.
it would be very nice..

Edit: Any Feisty  64er Users, is it working?
     Somone told me, it's lame...

---

### Post by inuwashi on 2007-03-12
If you do not have a nVidia / ATI video card I thought you should know that officially we are not up to the minimum requirements.

_To quote:_


[I][SIZE="2"]2. SYSTEM REQUIREMENTS
-=-=-=-=-=-=-=-=-=-=-=

    * Video/Graphics Card:
          o nVidia GeForce 2, GeForce 4mx, or better
          o OR ATI Radeon 8500, 9250, or better[/SIZE][/I]

_The error you get is: _

[I][SIZE="2"]PROBLEM 1:- Second Life fails to start up, with a warning on the console like:
   'Error creating window.' or
   'Unable to create window, be sure screen is set at 32-bit color' or
   'SDL: Couldn't find matching GLX visual.'[/SIZE][/I]

_and the official replay:_

[I][SIZE="2"]
SOLUTION:- Usually this indicates that your graphics card does not meet
   the minimum requirements, or that your system's OpenGL 3D graphics driver is
   not updated and configured correctly.  If you believe that your graphics
   card DOES meet the minimum requirements then you likely need to install the
   official so-called 'non-free' nVidia or ATI (fglrx) graphics drivers; we
   suggest one of the following options:
 * Consult your Linux distribution's documentation for installing these
   official drivers.  For example, Ubuntu provides documentation here:
   <https://help.ubuntu.com/community/BinaryDriverHowto>
 * If your distribution does not make it easy, then you can download the
   required Linux drivers straight from your graphics card manufacturer:
   - nVidia cards: <http://www.nvidia.com/object/unix.html>
   - ATI cards: <http://ati.amd.com/support/driver.html>[/SIZE][/I]

*Taken from the README-linux.txt file in the tarbal.... RTFM ](*,)*

Why oh why did I buy a machine with an Intel video card ... :-({|=

---

### Post by suoko on 2007-03-17
I have an INTEL GPU on my notebook and the game crashes indeed.
However the first SL version worked fine...

Now the game lauches but after a few seconds , X crashes and I can see the cursor of gdm which tries to reload but actually doesn't. I have to switch the pc off manually and restart.
using version 13_3_2

---

### Post by RacerII on 2007-03-18
> **sebi k said:**
> Said to eraly that it works.
The client starts but i can't connect.
It sais

And i can't go to the Support Forum, as mentioned above, because i never logged in.:( 
I quote the relevant console output

Any ideas, maybe another server to connect? But where to change??

Thanks :)

I have the same problem , did you find a solution?

2007-03-18T16:48:33Z WARNING: Alert: Unable to connect to Second Life.
2007-03-18T16:48:33Z DNS could not resolve the host name.
2007-03-18T16:48:33Z Please verify that you can connect to the [www.secondlife.com](www.secondlife.com)
2007-03-18T16:48:33Z web site.  If you can, but continue to receive this error,
2007-03-18T16:48:33Z please go to the support section and report this problem.

Edit:Fixed!

Need to change this line in /etc/modprobe.d/aliases

alias net-pf-10 ipv6
to
alias net-pf-10 off ipv6

Save and reboot , and it works fine now.

---

### Post by fsf@rula on 2007-03-26
I think the only problem with intel videocards is that direct rendering only works in16 bit depth mode. :evil: 
Actually, on linux, the game would probably run as well on intel cards as on nvidia/ati due to their lacking linux support and very bad quality linux drivers. :mad:

---

### Post by suoko on 2007-03-27
Forgot to apply what I was already suggested in the past.
It now works.

Here's what I have to do to run SL:

**In the shell script "secondlife" (in the main directory) you need to uncomment the line "export LL_GL_NOEXT=x" and then you should be fine.**

Remember you have to do this EVERYTIME a new SL version come out !!!!!!

---

### Post by dv5237 on 2007-03-27
1) I downloaded [http://secondlife.com/community/linux-alpha.php](http://secondlife.com/community/linux-alpha.php)
2) Then i unpacked the client
3) And finally i clicked on the second life script

It will run and im able to login but as soon as second life is "precaching" X freezes could somene give me some advise? If you need more details just ask.

---

### Post by heather on 2007-03-27
HI

no one in FreeBSd that i know uses second life but i know FreeBSD
is also LInux Compatiable so im asking any Ubuntu Users to help me please.

i am using FreeBSD and trying to get second life to work with it.
i have extracted the alpha version of SecondLife_i686_1_13_3_2.tar.bz2
and first off i dont see a .configure secondly when i did run

../secondlife i recieved this output in the terminal.


$ ./secondlife
bin/do-not-directly-run-secondlife-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

*********************************************************
This is an ALPHA release of the Second Life linux client.
Thank you for testing!
You can visit the Linux Client Alpha Testers forum at:
[http://forums.secondlife.com/forumdisplay.php?forumid=263](http://forums.secondlife.com/forumdisplay.php?forumid=263)
Please see README-linux.txt before reporting problems.

thank you if anyone can assist me :)

---

### Post by endre on 2007-03-27
Not sure why everyone is making such a fuss about this... SL works just great by running the secondlife shell - if you are having problems with crashes, let me assure you that it applies to everyone in there, no matter what client they use. It is just so crowded that they are having major stability issues in their systems.

---

### Post by suoko on 2007-03-28
> **dv5237 said:**
> 1) I downloaded [http://secondlife.com/community/linux-alpha.php](http://secondlife.com/community/linux-alpha.php)
2) Then i unpacked the client
3) And finally i clicked on the second life script

It will run and im able to login but as soon as second life is "precaching" X freezes could somene give me some advise? If you need more details just ask.


Try latest SL release 1.4.x.
If the problem continues, in the shell script "secondlife" (in the main directory) you need to uncomment the line "export LL_GL_NOEXT=x" and then you should be fine.

---

### Post by heather on 2007-03-28
Thank you very much for your very clear and understandable answer
to the question i have asked.

i willl uncomment tha part of the file then

Thank You

---

### Post by heather on 2007-03-29
i got second life to work by commenting out the export LL_GL_NOEXT=x

Most likely it was not working becasue i had uncommented that line earlier













---------------------------------------------FIXED PLEASE IGNORE BELOW----------------------------------------
Hi

i am still having trouble with second life
Please bare with me.i have not used Ubuntu in over a year
Since using freeBSD as my desktop and OpenBSD as my web server

i just installed Ubuntu this morning and when i ty to run second life
i get the following error

 Second Life appears to have crashed.
This crash reporter collects information about your computer's hardware, operating system, and some Second Life logs, which are used for debugging purposes only.
Sending crash reports is the best way to help us improve the quality of Second Life.
If you continue to experience this problem, please try one of the following:
- Contact support by email at [email]support@lindenlab.com[/email]
- If you can log-in, please contact Live Help by using menu Help > Live Help.
- Search the Second Life Knowledge Base at [http://secondlife.com/knowledgebase/](http://secondlife.com/knowledgebase/)





--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2007-03-29T06:57:44Z INFO: main: Viewer Digest: f8c697bf-d847-a47b-148c-12e89dd35a61
2007-03-29T06:57:44Z INFO: dump: Resend: 75
2007-03-29T06:57:44Z INFO: dump: Land: 85
2007-03-29T06:57:44Z INFO: dump: Wind: 17
2007-03-29T06:57:44Z INFO: dump: Cloud: 17
2007-03-29T06:57:44Z INFO: dump: Task: 223
2007-03-29T06:57:44Z INFO: dump: Texture: 223
2007-03-29T06:57:44Z INFO: dump: Asset: 110
2007-03-29T06:57:44Z INFO: dump: Total: 750
2007-03-29T06:57:44Z INFO: idle_startup: Initializing messaging system...
2007-03-29T06:57:44Z INFO: LLMessageSystem::loadTemplateFile: Message template checksum = 9a5fd87f
2007-03-29T06:57:44Z INFO: start_net: startNet - receive buffer size : 210944
2007-03-29T06:57:44Z INFO: start_net: startNet - send buffer size    : 210944
2007-03-29T06:57:44Z INFO: start_messaging_system: Message template version matches prehash version number
2007-03-29T06:57:44Z INFO: setAckThrottleBPS: LLXferManager ack throttle min rate: 2.66667e+06
2007-03-29T06:57:44Z INFO: setAckThrottleBPS: LLXferManager ack throttle actual rate: 2.93333e+06
2007-03-29T06:57:44Z INFO: setAckThrottleBPS: LLXferManager ack throttle min rate: 8000
2007-03-29T06:57:44Z INFO: setAckThrottleBPS: LLXferManager ack throttle actual rate: 150000
2007-03-29T06:57:44Z INFO: setUpstream: AssetStorage: Setting upstream provider to 0.0.0.0:12036
2007-03-29T06:57:44Z INFO: idle_startup: Initializing embedded web browser...
2007-03-29T06:57:45Z INFO: LLAudioEngine_FMOD::init() initializing FMOD
2007-03-29T06:57:45Z INFO: init: Trying ESD audio output...
2007-03-29T06:57:45Z WARNING: ESD audio output FAILED to initialize: Error initializing output device.
2007-03-29T06:57:45Z INFO: init: Trying OSS audio output...
2007-03-29T06:57:45Z WARNING: OSS audio output FAILED to initialize: Error initializing output device.
2007-03-29T06:57:45Z INFO: init: Trying ALSA audio output...
2007-03-29T06:57:45Z WARNING: ALSA audio output FAILED to initialize: Error initializing output device.
2007-03-29T06:57:45Z WARNING: Overall audio init failure.
2007-03-29T06:57:45Z WARNING: idle_startup: Unable to initialize audio engine
2007-03-29T06:57:46Z WARNING: signal_handlers: *** Caught signal 11
2007-03-29T06:57:46Z INFO: remove_marker_file()
2007-03-29T06:57:46Z INFO: do_elfio_glibc_backtrace: Opening stack trace file /home/electricity/.secondlife/logs/stack_trace.log
2007-03-29T06:57:46Z INFO: do_elfio_glibc_backtrace: Finished generating stack trace.
2007-03-29T06:57:47Z WARNING: LLTransferManager::~LLTransferManager - Should have been cleaned up by message system shutdown process

*********************************************************
This is an ALPHA release of the Second Life linux client.
Thank you for testing!
You can visit the Linux Client Alpha Testers forum at:
[http://forums.secondlife.com/forumdisplay.php?forumid=263](http://forums.secondlife.com/forumdisplay.php?forumid=263)
Please see README-linux.txt before reporting problems


Please help me

Thank You

---

### Post by eye208 on 2007-04-03
Here is some info about how to set up the SL viewer to get the most out of your ATI graphics card using the default fglrx driver (v8.28.8) from Edgy's repository. I successfully tested this with Radeon X800 GT (AGP) and Mobility Radeon X700 (PCIe) adapters.

In the startup script "secondlife" there are three statements to control the viewer's usage of OpenGL extensions. By default they look like this (v1.14.0.1):

export LL_GL_BASICEXT=x
#export LL_GL_NOEXT=x
#export LL_GL_BLACKLIST=abcdefghijklmno

Change these lines into this:

#export LL_GL_BASICEXT=x
#export LL_GL_NOEXT=x
export LL_GL_BLACKLIST=l

This will unlock the advanced graphics settings in the preferences dialog of the viewer. You can enable all the eyecandy that SL has to offer such as bump mapping, shiny surfaces, rippled water, avatar vertex program settings, local lighting, etc.

One setting you should keep disabled for now is VBO (vertex buffer objects). Enabling VBO does not cause crashes but seems to degrade framerate performance under certain conditions. My viewer sometimes slowed down to 1fps for extended periods of time with VBO enabled, making the game pretty much unplayable. Turning off VBO made the problem go away.

VBO might work for you if you use a more up-to-date version of fglrx, but you have to test that for yourself. Don't forget to post the results here! ;)

---

### Post by heather on 2007-04-03
[QUOTE=eye208;2395894]Here is some info about how to set up the SL viewer to get the most out of your ATI graphics card using the default fglrx driver (v8.28.8) from Edgy's repository. I successfully tested this with Radeon X800 GT (AGP) and Mobility Radeon X700 (PCIe) adapters.

Hi

Thanks for the extra advice

---

### Post by rugby82 on 2007-04-03
hallo guy!!!! i have too a problem about "second life"! when i clik on the icon for run program......it send me an error.........."WINDOW CREATION ERROR"!!!! what mean??!?

---

### Post by eye208 on 2007-04-04
> **rugby82 said:**
> "WINDOW CREATION ERROR"!!!! what mean??!?
It means you have not read this thread. ;)

Your current display driver has direct rendering disabled or does not support it in the first place.

---

### Post by Ian Adkins on 2007-04-11
Running Dapper, and I, too, am having a devil of a time trying to get SL to work.  I took care of the "window creation error," but now the program crashes while loading each and every time I try to run it:

Second Life appears to have crashed.
This crash reporter collects information about your computer's hardware, operating system, and some Second Life logs, which are used for debugging purposes only.
Sending crash reports is the best way to help us improve the quality of Second Life.
If you continue to experience this problem, please try one of the following:
- Contact support by email at [email]support@lindenlab.com[/email]
- If you can log-in, please contact Live Help by using menu Help > Live Help.
- Search the Second Life Knowledge Base at [http://secondlife.com/knowledgebase/](http://secondlife.com/knowledgebase/)
Send crash report?

I tried opening the shell, and I toggled each commented command, to no avail.  Tried asking the SL Linux Alpha forum, but no replies.

---

### Post by vradovic on 2007-04-27
I start secondlife and i can login but it is too slow.
my processor is 100% in use. (I have 3 GHz processor).

After 5 min just freeze. I have NVIDIA card with installed drivers. (128 MB). 


I try to comment and uncoment all this advice from this topic.

Can some one help?


regards,

---

### Post by vradovic on 2007-04-27
I start secondlife and I can login but it is too slow.
my processor is 100% in use. (I have 3 GHz processor).

After 5 min just freeze. I have NVIDIA card with installed drivers. (128 MB). 

I try to comment and uncoment all this advice from this topic.

Can some one help?

You can see my configuration in this attacment. 


regards,

---

### Post by vradovic on 2007-04-28
ok. I just buy 1GB more memory. Now i have 1.5 GB of ram and there is no more freezeing :)

but now i have second problem....


look my attacment

what is this?????????

---

### Post by suoko on 2007-05-01
I'm stuck now.

Old 14_0_1 version can't connect to SL anymore because upgrade is mandatory.

New one complains about this:

[I]bin/do-not-directly-run-secondlife-bin: error while loading shared libraries: libelfio.so: cannot open shared object file: No such file or directory

*********************************************************
This is an ALPHA release of the Second Life linux client.
Thank you for testing!
You can visit the Linux Client Alpha Testers forum at:
[http://forums.secondlife.com/forumdisplay.php?forumid=263](http://forums.secondlife.com/forumdisplay.php?forumid=263)
Please see README-linux.txt before reporting problems.[/I]

Is anyone in this situation ?

---

### Post by NULL712 on 2007-06-16
I can't figure out how to uninstall secondlife got it from getdeb.com I have a small HDD need to get some of my space back.

Thanx.

---

### Post by Robertjm on 2007-06-16
You should be able to just delete the whole directory where you installed secondlife and that will make it go away.

Remember to follow any symbolic links if you created one (example: I have a symbolic link of secondlife to the actual directory of secondlife--(whatever the rest of it is, which I can't remember).

Robert

> **NULL712 said:**
> I can't figure out how to uninstall secondlife got it from getdeb.com I have a small HDD need to get some of my space back.

Thanx.

---

### Post by TallTom on 2007-08-01
I tried running ./secondlife in the Terminal and this came up:

./secondlife: 52: bin/do-not-directly-run-secondlife-bin: not found

*********************************************************
This is an ALPHA release of the Second Life linux client.
Thank you for testing!
You can visit the Linux Client Alpha Testers forum at:
[http://forums.secondlife.com/forumdisplay.php?forumid=263](http://forums.secondlife.com/forumdisplay.php?forumid=263)
Please see README-linux.txt before reporting problems.


what is missing from the bin directory?

This is the version I'm trying to run:  
SecondLife_i686_1_18_0_6

---

### Post by s57nev on 2008-02-13
Anyone testing latest voice support in SL ? I'm using testing release. Other pepople say they can hear me but I can't hear them....


I have Nvidia CK8S audio driver. Anyone with similar experience ?

---

### Post by unbwogable on 2008-03-03
I'm having the same issue. I extracted everything right to my desktop, but when I double click the second life app, or ./secondlife it, I get nothing but a

---

### Post by gregj777 on 2008-03-22
> **williamts99 said:**
> I downloaded SecondLife_i686_1_12_2_9.tar.bz2 from the site, double clicked on the file, extracted to desktop, opened folder double clicked on file 'secondlife' and click on run, worked perfectly.

I did this and nothing happens. I'm running an ibook clamsheel G3 with 512kb of ram. Any ideas why it won't do anything? I double click the secondlife file and it just sits there, nothing happens.

---

### Post by s57nev on 2008-03-23
Well latest SL client has voice support and it works! It's WINDLIGHT testing version...

---

### Post by ecujak on 2008-04-10
//in terminal

cd SLdir
sudo ./secondlife

enter the password and go.....

---

### Post by thomashauk on 2008-04-18
> **TallTom said:**
> I tried running ./secondlife in the Terminal and this came up:

./secondlife: 52: bin/do-not-directly-run-secondlife-bin: not found

*********************************************************
This is an ALPHA release of the Second Life linux client.
Thank you for testing!
You can visit the Linux Client Alpha Testers forum at:
[http://forums.secondlife.com/forumdisplay.php?forumid=263](http://forums.secondlife.com/forumdisplay.php?forumid=263)
Please see README-linux.txt before reporting problems.


what is missing from the bin directory?

This is the version I'm trying to run:  
SecondLife_i686_1_18_0_6

Are you running the 64 bit version of Ubuntu as I have found that that is the problem. Don't know how to fix it though.

---

### Post by promix89 on 2008-05-10
I downloaded version Second Life 1.19.1 (4), but when I look install so that nothing like that and then left ...

ionel@ionel-desktop:~/temp/sl$ sudo ./secondlife
[sudo] password for ionel: 
Running from /home/ionel/temp/sl
2008-05-10T05:53:10Z INFO: anotherInstanceRunning: Checking marker file for lock...
2008-05-10T05:53:10Z INFO: anotherInstanceRunning: Marker file isn't locked.
2008-05-10T05:53:10Z INFO: initMarkerFile: Checking marker file for lock...
2008-05-10T05:53:10Z WARNING: ll_apr_warn_status: APR: No such file or directory
2008-05-10T05:53:10Z WARNING: ll_apr_warn_status: APR: No such file or directory
2008-05-10T05:53:10Z WARNING: ll_apr_warn_status: APR: No such file or directory
2008-05-10T05:53:10Z INFO: anotherInstanceRunning: Checking marker file for lock...
2008-05-10T05:53:10Z INFO: anotherInstanceRunning: Marker file isn't locked.
2008-05-10T05:53:10Z INFO: initMarkerFile: Exec marker found: program froze on previous execution
2008-05-10T05:53:10Z INFO: initMarkerFile: Marker file created.
2008-05-10T05:53:10Z INFO: initMarkerFile: Marker file locked.
2008-05-10T05:53:10Z INFO: Exiting initMarkerFile().
2008-05-10T05:53:10Z INFO: initConfiguration: Last execution froze, requesting to send crash report.
2008-05-10T05:53:10Z INFO: ll_try_gtk_init: Starting GTK Initialization.
2008-05-10T05:53:10Z INFO: ll_try_gtk_init: GTK Initialized.
2008-05-10T05:53:10Z INFO: ll_try_gtk_init: - Compiled against GTK version 2.4.14
2008-05-10T05:53:10Z INFO: ll_try_gtk_init: - Running against GTK version 2.12.9
2008-05-10T05:53:10Z INFO: OSMessageBoxSDL: Creating a dialog because we're in windowed mode and GTK is happy.
2008-05-10T05:53:49Z INFO: initConfiguration: Sending crash report.
2008-05-10T05:53:49Z INFO: fork: Forked child process 6393
2008-05-10T05:53:49Z INFO: LLApp::setupErrorHandling - Starting error thread
2008-05-10T05:53:49Z INFO: run: thread_error - Waiting for an error
Can't find file /root/.secondlife/logs/stack_trace.log
Can't find file /root/.secondlife/user_settings/settings.xml
Can't find file /root/.secondlife/logs/stack_trace.log
Can't find file /root/.secondlife/logs/stats.log
2008-05-10T05:53:59Z INFO: writeSystemInfo: Second Life version 1.19.1
2008-05-10T05:53:59Z INFO: writeSystemInfo: Local time: 2008-05-10T08:53:59 EEST
2008-05-10T05:53:59Z INFO: writeSystemInfo: CPU info:
processor	: 0 vendor_id	: AuthenticAMD cpu family	: 6 model	: 4 model name	: AMD Athlon(tm)  stepping	: 2 cpu MHz		: 899.219 cache size	: 256 KB fdiv_bug	: no hlt_bug		: no f00f_bug	: no coma_bug	: no fpu		: yes fpu_exception	: yes cpuid level	: 1 wp		: yes flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up bogomips	: 1800.87 clflush size	: 32  
->mHasSSE:     0
->mHasSSE2:    0
->mHasAltivec: 0
->mCPUMhz:     899
->mCPUString:  AMD Athlon(tm) 

2008-05-10T05:53:59Z INFO: writeSystemInfo: Memory info:
MemTotal:      1035400 kB MemFree:        411848 kB Buffers:         18124 kB Cached:         347496 kB SwapCached:          0 kB Active:         308660 kB Inactive:       275916 kB HighTotal:      131008 kB HighFree:          252 kB LowTotal:       904392 kB LowFree:        411596 kB SwapTotal:      345388 kB SwapFree:       345388 kB Dirty:             336 kB Writeback:           0 kB AnonPages:      218904 kB Mapped:          73972 kB Slab:            17336 kB SReclaimable:     9716 kB SUnreclaim:       7620 kB PageTables:       1812 kB NFS_Unstable:        0 kB Bounce:              0 kB CommitLimit:    863088 kB Committed_AS:   606552 kB VmallocTotal:   114680 kB VmallocUsed:     30244 kB VmallocChunk:    78836 kB 
2008-05-10T05:53:59Z INFO: writeSystemInfo: OS: Linux 2.6
2008-05-10T05:53:59Z INFO: writeSystemInfo: OS info: Linux 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
2008-05-10T05:53:59Z INFO: init: Loading configuration file /root/.secondlife/user_settings/settings.xml
2008-05-10T05:53:59Z WARNING: parseFile: Couldn't open file /root/.secondlife/user_settings/settings.xml
2008-05-10T05:53:59Z WARNING: parseFile: LLXmlTree parse failed.  Line 1: Couldn't open file /root/.secondlife/user_settings/settings.xml
2008-05-10T05:53:59Z WARNING: loadFromFile: Unable to open control file /root/.secondlife/user_settings/settings.xml
2008-05-10T05:53:59Z INFO: init: Failed to load settings from /root/.secondlife/user_settings/settings.xml
2008-05-10T05:53:59Z INFO: init: Loading legacy settings from /root/.secondlife/user_settings/settings.ini
2008-05-10T05:53:59Z INFO: loadFromFileLegacy: LLControlGroup::loadFromFile unable to open.
2008-05-10T05:53:59Z WARNING: parseFile: Couldn't open file /root/.secondlife/user_settings/crash_settings.xml
2008-05-10T05:53:59Z WARNING: parseFile: LLXmlTree parse failed.  Line 1: Couldn't open file /root/.secondlife/user_settings/crash_settings.xml
2008-05-10T05:53:59Z WARNING: loadFromFile: Unable to open control file /root/.secondlife/user_settings/crash_settings.xml
2008-05-10T05:53:59Z INFO: init: Loading art table from /home/ionel/temp/sl/app_settings/viewerart.xml
2008-05-10T05:53:59Z INFO: init: Loading art table from /home/ionel/temp/sl/skins/textures/textures.xml
2008-05-10T05:53:59Z INFO: init: Loading base colors from /home/ionel/temp/sl/app_settings/colors_base.xml
2008-05-10T05:53:59Z INFO: init: Loading user colors from /home/ionel/temp/sl/app_settings/colors.xml
2008-05-10T05:53:59Z INFO: init: Failed to load user colors from /home/ionel/temp/sl/app_settings/colors.xml
2008-05-10T05:53:59Z INFO: init: Loading legacy colors from /home/ionel/temp/sl/app_settings/colors.ini
2008-05-10T05:54:00Z INFO: update_vector_performances: Vectorization         : DISABLED
2008-05-10T05:54:00Z INFO: update_vector_performances: Vector Processor      : COMPILER DEFAULT
2008-05-10T05:54:00Z INFO: update_vector_performances: Vectorized Skinning   : ENABLED
2008-05-10T05:54:00Z INFO: update_vector_performances: Vectorization         : DISABLED
2008-05-10T05:54:00Z INFO: update_vector_performances: Vector Processor      : COMPILER DEFAULT
2008-05-10T05:54:00Z INFO: update_vector_performances: Vectorized Skinning   : DISABLED
2008-05-10T05:54:00Z INFO: purgeCache: Purging Texture Cache...
2008-05-10T05:54:00Z WARNING: ll_apr_warn_status: APR: No such file or directory
2008-05-10T05:54:00Z WARNING: ll_apr_warn_status: APR: No such file or directory
2008-05-10T05:54:00Z INFO: purgeCache: Purging Cache...
2008-05-10T05:54:00Z INFO: initCache: TEXTURE CACHE: Headers: 139810 Textures size: 320 MB
2008-05-10T05:54:00Z INFO: initCache: VFS CACHE SIZE: 100 MB
2008-05-10T05:54:00Z WARNING: initCache: Bad or missing vfx index file /root/.secondlife/cache/index.db2.x.1
2008-05-10T05:54:00Z WARNING: initCache: Removing old vfs data file /root/.secondlife/cache/data.db2.x.1
2008-05-10T05:54:00Z INFO: initCache: Removing old vfs and re-sizing
2008-05-10T05:54:00Z INFO: presizeDataFile: Pre-sized VFS data file to 104857600 bytes
2008-05-10T05:54:00Z INFO: LLVFS: VFS: Using index file /root/.secondlife/cache/index.db2.x.294466487 and data file /root/.secondlife/cache/data.db2.x.294466487
2008-05-10T05:54:00Z INFO: LLVFS: VFS: Using index file /home/ionel/temp/sl/app_settings/static_index.db2 and data file /home/ionel/temp/sl/app_settings/static_data.db2
2008-05-10T05:54:00Z INFO: initWindow: Initializing window...
2008-05-10T05:54:00Z INFO: createContext, fullscreen=0 size=1000x700
2008-05-10T05:54:00Z INFO: createContext: Compiled against SDL 1.2.5
2008-05-10T05:54:00Z INFO: createContext:  Running against SDL 1.2.12
2008-05-10T05:54:00Z INFO: createContext: creating window 1000x700x32
2008-05-10T05:54:00Z INFO: x11_detect_VRAM_kb: Looking in /var/log/Xorg.0.log for VRAM info...
2008-05-10T05:54:00Z INFO: createContext: X11 log-parser detected 256MB VRAM.
2008-05-10T05:54:00Z INFO: createContext: GL buffer:
2008-05-10T05:54:00Z INFO: createContext:   Red Bits 8
2008-05-10T05:54:00Z INFO: createContext:   Green Bits 8
2008-05-10T05:54:00Z INFO: createContext:   Blue Bits 8
2008-05-10T05:54:00Z INFO: createContext:   Alpha Bits 8
2008-05-10T05:54:00Z INFO: createContext:   Depth Bits 24
2008-05-10T05:54:00Z INFO: createContext:   Stencil Bits 8
2008-05-10T05:54:00Z INFO: initExtensions: Couldn't initialize GL_EXT_paletted_texture
2008-05-10T05:54:00Z INFO: initExtensions: GL Probe: Getting symbols
2008-05-10T05:54:00Z INFO: initExtensions: GL Probe: Got symbols
2008-05-10T05:54:00Z INFO: LLViewerWindow: Loading feature tables.
2008-05-10T05:54:00Z INFO: loadGPUClass: GPU is NVIDIA GeForce FX 5500
2008-05-10T05:54:00Z INFO: applyBaseMasks: Setting GPU Class to Class0
2008-05-10T05:54:00Z INFO: maskFeatures: Applying Feature Mask: Class0
2008-05-10T05:54:00Z INFO: maskFeatures: Applying Feature Mask: NVIDIA_GeForce_FX_5500
2008-05-10T05:54:00Z INFO: maskFeatures: Applying Feature Mask: CPUSlow
2008-05-10T05:54:00Z INFO: applyRecommendedSettings: Applying Recommended Features
2008-05-10T05:54:00Z INFO: applyBaseMasks: Setting GPU Class to Class0
2008-05-10T05:54:00Z INFO: maskFeatures: Applying Feature Mask: Class0
2008-05-10T05:54:00Z INFO: maskFeatures: Applying Feature Mask: NVIDIA_GeForce_FX_5500
2008-05-10T05:54:00Z INFO: maskFeatures: Applying Feature Mask: CPUSlow
2008-05-10T05:54:00Z INFO: maskFeatures: Applying Feature Mask: Low
2008-05-10T05:54:00Z WARNING: applyFeatures: AHHH! Control setting RenderNightBrightness does not exist!
2008-05-10T05:54:00Z INFO: LLViewerImageList::doPreloadImages: Preloading images...

Please help me!!!

---

### Post by random753 on 2008-06-24
I am very new to Ubuntu. I simply downloaded the linux version of Second Life to desktop. opened the file. double clicked the second life file that you see with others on the bottom right side..  That opened a choice to "play in terminal". ...Thats all. It ran perfectly for hours without a crash.

You should do a more involved install because you will want to save pictures and files etc but thats a quick way to get SL running on Ubuntu.

I should say i have 4 gigs of ram and a core2 processor and a Nvidia 8800 with 1 gig video ram so my machine is a lot more able than most.

---

### Post by caseygibbs on 2008-07-19
My issue is that when I start the program, from terminal, it hangs while loading the license agreement - I can't agree to it and start, I can only cancel out.

---

### Post by JusKrusin on 2009-05-02
Hope this helps out. You might wanna pin it.
 
Second Life - Linux Beta README
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
This document contains information about the Second Life Linux
client, and isn't meant to serve as an introduction to Second
Life itself - please see <[http://www.secondlife.com/whatis/](http://www.secondlife.com/whatis/)>.
1. Introduction
2. System Requirements
3. Installing & Running
4. Known Issues
5. Troubleshooting
5.1. 'Error creating window.'
5.2. System hangs
5.3. Blank window after minimizing it
5.4. Audio
5.5. 'Alt' key for camera controls doesn't work
5.6. In-world movie playback
6. Advanced Troubleshooting
6.1. Audio
6.2. OpenGL
7. Obtaining and working with the client source code
8. Getting more help, and reporting problems
 
1. INTRODUCTION
-=-=-=-=-=-=-=-
Hi! This is a BETA release of the Second Life client for Linux.
The 'beta' status means that although we're still smoothing-out a few rough
edges, this version of the client is functionally complete and should
work quite well 'out of the box' for accessing Second Life.
We encourage you to try it out and let us know of its compatibility
with your system. Be aware that although this is a 'beta' client, it connects
to the main Second Life world and changes you make there are permanent.
You will have either obtained this client from secondlife.com (the official
site) or from a third-party packager; if you encounter any problems then
we recommend trying the latest official builds from secondlife.com which are
updated often.
Please enjoy!
 
2. SYSTEM REQUIREMENTS
-=-=-=-=-=-=-=-=-=-=-=
Minimum requirements:
* Internet Connection: Cable or DSL
* Computer Processor: 800MHz Pentium III or Athlon or better
(recommended: 1.5GHz or more)
* Computer Memory: 512MB (recommended: 768MB or more)
* Linux Operating System: A reasonably modern 32-bit Linux environment
is required. If you are running a 64-bit Linux distribution then
you will need its 32-bit compatibility environment installed.
* Video/Graphics Card:
o nVidia GeForce 2, GeForce 4mx, or better (recommend one of the
following: 6700, 6800, 7600, 7800, 7900, 8400, 8500, 8600,
8800, Go 7400, Go 7600, Go 7800, Go 7900)
o OR ATI Radeon 8500, 9250, or better
(nVidia cards are recommended for the Linux client)
**NOTE**: Second Life absolutely requires you to have recent, correctly-
configured OpenGL 3D drivers for your hardware - the graphics drivers
that came with your operating system may not be good enough! See the
TROUBLESHOOTING section if you encounter problems starting Second Life.
For a more comfortable experience, the RECOMMENDED hardware for the Second
Life Linux client is very similar to that for Windows, as detailed at:
<[https://secondlife.com/corporate/sysreqs.php](https://secondlife.com/corporate/sysreqs.php)>
 
3. INSTALLING & RUNNING
-=-=-=-=-=-=-=-=-=-=-=-
The Second Life Linux client entirely runs out of the directory you have
unpacked it into - no installation step is required.
Run ./secondlife from the installation directory to start Second Life.
For in-world MOVIE PLAYBACK, you will need GStreamer 0.10 installed on your
system. This is optional - it is not required for general client
functionality. If you have GStreamer 0.10 installed, the selection of
in-world movies you can successfully play will depend on the GStreamer
plugins you have; if you cannot play a certain in-world movie then you are
probably missing the appropriate GStreamer plugin on your system - you may
be able to install it (see TROUBLESHOOTING).
User data is stored in the hidden directory ~/.secondlife by default; you may
override this location with the SECONDLIFE_USER_DIR environment variable if
you wish.
 
4. KNOWN ISSUES
-=-=-=-=-=-=-=-
These are the most commonly-encountered known issues which are specific to
the Beta release of the Linux client.
* UPLOAD / SAVE / COLOR-PICKER DIALOGS - These only appear when the client
is in 'windowed' mode, not 'fullscreen' mode.
* UPDATING - when the client detects that a new version of Second Life
is available, it will ask you if you wish to download the new version.
This option is not implemented; to upgrade, you should manually download a
new version from the Second Life web site, <[http://www.secondlife.com/](http://www.secondlife.com/)>.
 
5. TROUBLESHOOTING
-=-=-=-=-=-=-=-=-=
The client prints a lot of diagnostic information to the console it was
run from. Most of this is also replicated in ~/.secondlife/logs/SecondLife.log
- this is helpful to read when troubleshooting, especially 'WARNING' lines.
VOICE PROBLEMS? See the separate README-linux-voice.txt file for Voice
troubleshooting information.
PROBLEM 1:- Second Life fails to start up, with a warning on the console like:
'Error creating window.' or
'Unable to create window, be sure screen is set at 32-bit color' or
'SDL: Couldn't find matching GLX visual.'
SOLUTION:- Usually this indicates that your graphics card does not meet
the minimum requirements, or that your system's OpenGL 3D graphics driver is
not updated and configured correctly. If you believe that your graphics
card DOES meet the minimum requirements then you likely need to install the
official so-called 'non-free' nVidia or ATI (fglrx) graphics drivers; we
suggest one of the following options:
* Consult your Linux distribution's documentation for installing these
official drivers. For example, Ubuntu provides documentation here:
<[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)>
* If your distribution does not make it easy, then you can download the
required Linux drivers straight from your graphics card manufacturer:
- nVidia cards: <[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)>
- ATI cards: <[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)>
PROBLEM 2:- My whole system seems to hang when running Second Life.
SOLUTION:- This is typically a hardware/driver issue. The first thing to
do is to check that you have the most recent official drivers for your
graphics card (see PROBLEM 1).
SOLUTION:- Some residents with ATI cards have reported that running
'sudo aticonfig --locked-userpages=off' before running Second Life solves
their stability issues.
SOLUTION:- As a last resort, you can disable most of Second Life's advanced
graphics features by editing the 'secondlife' script and removing the '#'
from the line which reads '#export LL_GL_NOEXT=x'
PROBLEM 3:- After I minimize the Second Life window, it's just blank when
it comes back.
SOLUTION:- Some Linux desktop 'Visual Effects' features are incompatible
with Second Life. One reported solution is to use your desktop
configuration program to disable such effects. For example, on Ubuntu 7.10,
use the desktop toolbar menu to select System -> Preferences -> Appearance,
then change 'Visual Effects' to 'None'.
PROBLEM 4:- Music and sound effects are silent or very stuttery.
SOLUTION:- The most common solution is to ensure that you have the 'esd'
program (part of the 'esound' package) installed and running before you
start Second Life. Users of Ubuntu (and some other) Linux systems can
simply run the following to install and configure 'esound':
sudo apt-get install esound
For others, simply running 'esd&' from a command-line should get it running.
PROBLEM 5:- Using the 'Alt' key to control the camera doesn't work or just
moves the Second Life window.
SOLUTION:- Some window managers eat the Alt key for their own purposes; you
can configure your window manager to use a different key instead (for
example, the 'Windows' key!) which will allow the Alt key to function
properly with mouse actions in Second Life and other applications.
PROBLEM 6:- In-world movie playback doesn't work for me.
SOLUTION:- You need to have a working installation of GStreamer 0.10; this
is usually an optional package for most versions of Linux. If you have
installed GStreamer 0.10 and you can play some movies but not others then
you need to install a wider selection of GStreamer plugins, either
from your vendor or an appropriate third party.
 
6. ADVANCED TROUBLESHOOTING
-=-=-=-=-=-=-=-=-=-=-=-=-=-
The 'secondlife' script which launches Second Life contains some
configuration options for advanced troubleshooters.
* AUDIO - Edit the 'secondlife' script and you will see three audio
options: LL_BAD_ESD, LL_BAD_OSS, LL_BAD_ALSA. Second Life tries to
use ESD, OSS, then ALSA audio drivers in this order; you may uncomment
the corresponding LL_BAD_* option to skip an audio driver which you
believe may be causing you trouble.
* OPENGL - For advanced troubleshooters, the LL_GL_BLACKLIST option lets
you disable specific GL extensions, each of which is represented by a
letter ("a"-"o"). If you can narrow down a stability problem on your system
to just one or two GL extensions then please post details of your hardware
(and drivers) to the Linux Client Testers forum (see link below) along
with the minimal LL_GL_BLACKLIST which solves your problems. This will help
us to improve stability for your hardware while minimally impacting
performance.
LL_GL_BASICEXT and LL_GL_NOEXT should be commented-out for this to be useful.
 
7. OBTAINING AND WORKING WITH THE CLIENT SOURCE CODE
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
We're pleased to have released the Second Life client's source code under
an Open Source license compatible with the 'GPL'. To get involved with client
development, please see:
<[http://wiki.secondlife.com/wiki/Open_Source_Portal](http://wiki.secondlife.com/wiki/Open_Source_Portal)>
 
8. GETTING MORE HELP AND REPORTING PROBLEMS
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
For general help and support with Second Life:
<[http://secondlife.com/community/support.php](http://secondlife.com/community/support.php)>
For problems and discussion concerning unofficial (not secondlife.com)
releases, please contact your packager or the SLDev mailing list:
<[https://lists.secondlife.com/cgi-bin/mailman/listinfo/sldev](https://lists.secondlife.com/cgi-bin/mailman/listinfo/sldev)>
In-world help: Please use the 'Help' menu in the client for various
non-Linux-specific Second Life help options.
In-world discussion: There is a 'Linux Client Users' group
inside Second Life which is free to join. You can find it by pressing
the 'Search' button at the bottom of the window and then selecting the
'Groups' tab and searching for 'Linux'. This group is useful for discussing
Linux issues with fellow Linux client users who are online.
The Second Life Issue Tracker:
<[http://jira.secondlife.com/](http://jira.secondlife.com/)>
This is the right place for finding known issues and reporting new
bugs in all Second Life releases if you find that the Troubleshooting
section in this file hasn't helped (please note, however, that this is
not a support forum).
Linux Client Testers forum:
<[http://forums.secondlife.com/forumdisplay.php?forumid=263](http://forums.secondlife.com/forumdisplay.php?forumid=263)>
This is a forum where Linux Client users can help each other out and
discuss the latest updates.
--------------------------------------------------------------------------------

---

### Post by JusKrusin on 2009-05-02
[COLOR=#cc6633]Second Life - Linux Voice Support README
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

WHAT IS IT?
-=-=-=-=-=-

Linux Voice Support is a new feature in testing which allows users
of the Linux Second Life client to participate in voice-chat with other
residents and groups inside Second Life, with an appropriate
headset/microphone.

Linux Voice Support is currently EXPERIMENTAL and is known to still
have some compatibility issues.

REQUIREMENTS
-=-=-=-=-=-=

* A headset/microphone supported by your chosen version of Linux
* The ALSA sound system (you probably already have this -
i.e. the alsa-base and alsa-utils packages on Ubuntu)

Success with Linux Voice support has been reported on the following
systems:
* Ubuntu 7.04 (Feisty) with USB Plantronics headset
* Ubuntu 7.04 (Feisty) with Intel HDA audio chipset
* Ubuntu 6.06 (Dapper) with Intel ICH5/CMI9761A+ audio chipset
* Ubuntu 6.06 (Dapper) with SigmaTel STAC2997 audio chipset
* Fedora Core 6 with (unknown) audio chipset

Problems with Linux Voice support have been reported on the following
systems:
* Ubuntu 6.06 (Dapper) with Creative EMU10K1 audio chipset

KNOWN PROBLEMS
-=-=-=-=-=-=-=

* The 'Input Level' meter in the Voice Chat Device Settings dialog
does not respond to audio input.

TROUBLESHOOTING
-=-=-=-=-=-=-=-

PROBLEM 1: I don't see a white dot over the head of my avatar or other
Voice-using avatars.
SOLUTION:
a. Ensure that 'Enable voice chat' is enabled in the Voice Chat
preferences window and that you are in a voice-enabled area (you
will see a blue headphone icon in the SL menu-bar).
b. If the above does not help, exit Second Life and ensure that any
remaining 'SLVoice' processes (as reported by 'ps', 'top' or similar)
are killed.

PROBLEM 2: I have a white dot over my head but I never see (or hear!) anyone
except myself listed in the Active Speakers dialog when I'm sure that other
residents nearby are active Voice users.
SOLUTION: This is an incompatibility between the Voice support and your
system's audio (ALSA) driver version/configuration.
a. Back-up and remove your ~/.asoundrc file, re-test.
b. Check for updates to your kernel, kernel modules and ALSA-related
packages using your Linux distribution's package-manager - install these,
reboot and re-test.
c. Update to the latest version of ALSA manually. For a guide, see the
'Update to the Latest Version of ALSA' section of this page:
<https://help.ubuntu.com/community/HdaIntelSoundHowto> or the official
documentation on the ALSA site: <http://www.alsa-project.org/> - reboot
and re-test.

PROBLEM 3: I can hear other people, but they cannot hear me.
SOLUTION:
a. Ensure that you have the 'Talk' button activated while you are trying to
speak.
b. Ensure that your microphone jack is inserted into the correct socket of your
sound card, where appropriate.
c. Use your system mixer-setting program or the 'alsamixer' program to ensure
that microphone input is set as the active input source and is not muted.
d. Verify that audio input works in other applications, i.e. Audacity

PROBLEM 4: Other people just hear bursts of loud noise when I speak.
SOLUTION:
a. Use your system mixer-setting program or the 'alsamixer' program to ensure
that microphone Gain/Boost is not set too high.

FURTHER PROBLEMS?
-=-=-=-=-=-=-=-=-

Please report further issues to the public Second Life issue-tracker
at <http://jira.secondlife.com/> (please note, however, that this is not
a support forum).[/COLOR]

---

### Post by coldmack on 2009-05-27
I guess the problem I have is I installed the latest version for my hard device, but Second Life software at log in is telling me to upgrade to the new version. Problem is, the new version is for Jaunty and when I try to install it I get this dependency not satisfiable: libgtk2.0-0
Synaptic shows I have libgtk1.2 and libgtk2.0-0 installed, so not sure what the real issue is here. Is there like a newer version of libgtk I have to some how install or something? Any ideas? thanks.

---

### Post by coldmack on 2009-05-28
any ideas?

---

### Post by Naiki Muliaina on 2009-05-30
> **coldmack said:**
> I guess the problem I have is I installed the latest version for my hard device, but Second Life software at log in is telling me to upgrade to the new version. Problem is, the new version is for Jaunty and when I try to install it I get this dependency not satisfiable: libgtk2.0-0
Synaptic shows I have libgtk1.2 and libgtk2.0-0 installed, so not sure what the real issue is here. Is there like a newer version of libgtk I have to some how install or something? Any ideas? thanks.

Are you installing it through the repo _**[(omvvviewer repo)]("http://naiux.wordpress.com/2008/11/30/cracking-news-on-second-life-front/")**_ or just the standard download client from the SL website?

And jesus thread necromancy ^^

---

### Post by coldmack on 2009-05-30
The latest hardy deb from getdeb.net. should I be doing it from the repos or something?

Alright I just looked it up I do have that software omvviewer installed, but it was done via a different repo or something. I am on the HP version of Hardy so I get the custom HP interface an not the standard Ubuntu desktop so I am not sure where I would find the omvviewer software, unless I run it from terminal? 

Edit: I tried it via terminal nothing. :\

---

### Post by boldwing2923 on 2010-09-17
i tried to run it and all i keep getting is: window creation error...can anyone help me>?

---

### Post by boldwing2923 on 2010-09-17
i also tried to install the snowglobe and i keep getting the same thing

---

### Post by boldwing2923 on 2010-09-17
i tried to do that and i just keep getting a window creation error

---

### Post by Naiki Muliaina on 2010-09-17
Ok, old thread... Really chuffin old actually...

What Ubuntu are you using? Version number and 32 bit or 64 bit? What graphics driver do you have installed? What version of second life are you trying to use? The newest one off the website or a 3rd party one?

---

### Post by okirun on 2010-11-25
I tried downloading Second Life for Linux/Ubuntu, and I follow the directions a previous poster on here gave 

...but when I got to the part where I have the second life folder on my desktop and I click Open and then I click Run for the file "second life" that it contains... it starts to run but it stops and closes with no warning at all. :/ ?? I don't understand.

I've been looking at this thread for a long time now and no one mentions this problem at all.

---

### Post by eMosso on 2012-03-20
I noticed a serious degradation in quality when running SL in Ubuntu as compared to WindowsXP, thought maybe I did something wrong, but apparently not judging by the advice given so far. It's hella buggy for me, but ya kinda' sorta works in very minimal ways.

---

