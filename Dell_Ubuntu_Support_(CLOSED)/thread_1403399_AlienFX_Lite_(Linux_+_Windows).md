---
title: "AlienFX Lite (Linux + Windows)"
date: 2010-02-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Wattos on 2010-02-10
Hi,

Since I received my Allpowerfull M15x laptop, I always wanted to use the alienFX lights as an indicator of whether I am currently busy or available to talk to/etc... The solution provided by alienware would be to load up the alienFX software (takes a relative long time), load up a previously created profile, hit the apply button and exit the application. Suffice to say that this is really impractical to be of any use. The other major problem was that I use mainly Linux as my working environment and alienfx is not available for linux and the alienware software seems  not to work on Windows over a virtual machine installed(tried both Vmware and VMBox).

Thus I decided to write my own alienFX program which would work under Windows and Linux. Here is the Result

I would be grateful for any comments and opinions on how to make the application better. Also, please let me know if you think the application is useless, so that I know if there is any point in further developing this application.

[B][CENTER]****DISCLAIMER****[/CENTER]
THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

USE THIS SOFTWARE ON YOUR OWN RISK!
[/B]

**[SIZE="5"]AlienFX Lite[/SIZE]**


Revision History: 
```
Date       | Description            | version  | url
15/03/2010 | Forth  Verison         | 0.4b     | http://progger.co.uk/alienfx/AlienFXLite-0.4b.jar
12/02/2010 | Third  Verison         | 0.3      | http://progger.co.uk/alienfx/AlienFXLite-0.3.jar
12/02/2010 | Second Verison         | 0.2      | http://progger.co.uk/alienfx/AlienFXLite-0.2.jar
10/02/2010 | First version released | 0.1      |  http://progger.co.uk/alienfx/AlienFXLite-0.1.jar 
```  


**Description:**
AlienFX Lite is a simple cross-platform program to create profiles and set the AlienFX lightning to the set colors. This application was done for the Allpowerfull M15x and only tested on this machine. It should also work on the M17x. The application will most likely accept the Area 51 m15x but it was untested. The current supported platforms are:
Linux (32 bit), Linux(64 bit), Mac OS X(UNTESTED), Windows 7(64 bit), Windows 7 (32 bit), Windows Vista (32bit), Windows Vista 64bit, Windows XP

**Special Thanks:**
Thanks go to Ingrater ([http://3d.benjamin-thaut.de/](http://3d.benjamin-thaut.de/)) for providing me with the protocol for the alienFX device and some windows native code. 

**Installation:**
The application can be installed on windows and on linux in the following way.

Linux: (Ubuntu)

This guide is for ubuntu only. For a different distribution (which doesnt use debian packages), you have to install the following things Java Runtime Environment 1.6 (6) and libusb-1.0-0. 

Step 1) ==CHECK FOR JVM 1.6==
Check if you have have a java vm installed. This can be done by typing "java -version" into a terminal. If you get a "command not found" returned or the version is lower than 1.6 go to step 2. If the version is 1.6 or above, go to step 3.

Step 2) ==INSTALLING JVM==
To install the latest jvm type:

```
sudo apt-get install openjdk-6-jre
```

Confirm your choice and wait until its installed.

Step 3) ==INSTALL libusb-1.0==
The linux native libraries are based of libusb. It has to be present on the system. This can be done by:

```
sudo apt-get install libusb-1.0-0
```


Windows:

Step 1) If you dont have java 1.6 then Go to: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) and click on Download JRE. Install the JRE.

Step 2) Place the AlienFXLite-0.1.jar into a suitable for you folder, and remember the path (e.g. C:\User\wattos\AlienFXLite-0.1.jar)

Step 3) Unfortunately the application requires administrator powers or othrwise it will not be able to write to the alienfx device. Find the location of the JRE javaw.exe, which will most likely be somewhere here: C:\Program Files (x86)\Java\jdk1.6.0_18\bin\javaw.exe

Step 4) Right click on your desktop, and do new->Shortcut. Now enter the path (e.g. "C:\Program Files (x86)\Java\jdk1.6.0_18\bin\javaw.exe") with the qoutes into the text field, followed by the location of the jar file. Thus all together it should look like:

```
"C:\Program Files (x86)\Java\jdk1.6.0_18\bin\javaw.exe" -jar "C:\User\wattos\AlienFXLite-0.1.jar" 
```

If you want the application to go directly to the system tray without opening, append an -s e.g.

```
"C:\Program Files (x86)\Java\jdk1.6.0_18\bin\javaw.exe" -jar "C:\User\wattos\AlienFXLite-0.1.jar" -s
```

Thats it, you are done.

**Manual:**
To open the application in linux, do the following 
sudo java -jar AlienFXLite-0.1.jar 
or
sudo java -jar AlienFXLite-0.1.jar -s 
for the silent version. 

On windows, rightclick on the created shortcut and press on "**run as admin**". 


Once the application is open, you can create new profiles. On the left you can see the color chooser, which is used to choose colors. When creating a new profile while having no profile selected, all lights will be defaulted to the color which was selected when pressing the new profile button. If you create a new profile while another profile is selected, then a copy of that profile will be created. 

Once you are happy with a profile you need to press the save button. This will write the changes to the hdd. The remove button allows you to remove profiles. Finally, click the apply button to apply the profile to the alienFX controller. 

If System trays are supported (usually they are) the application will not close when the window is closed. Instead it will hide. The application is only closable from the system tray. To close the application, right click on the system tray alienFX icon and then Exit. In this small menu, all profiles are also listed. Clicking on a profiles name will automatically apply the profile without having to open the applications window. 

In order to change the colors for selected regions, select a color on the left side, then press the button with the text of the region you want to change the color. Dont forget to hit the save buttons once you are happy with a profile. The apply button DOES not save your profile. 

**Video Tutorial**
[http://www.youtube.com/watch?v=3SPJAFx5Meo](http://www.youtube.com/watch?v=3SPJAFx5Meo)

**Misc:**

* The profiles are saved under (USER_HOME)/.alienFXprofiles.
* On linux you can make your user able to access the usb devices without being a super user but part of a group which has access to the usb devices. I dont know how to do that


**Known Issues:**
* Sometimes the JVM will spit out a bug when opening the menu of the system tray. This is a bug in Swing and should be fixed with a new update of the JRE (hopefully). 
* It seems that the system look and feel does not work on ubuntu which runs inside a VM (??).
* With some look and feels, its possible that the non-resizable window is too small. 
* The java functionality for system trays is generally crap. The balloon messages looks really bad and icon does not support transparency.
* It only works with the 32 bit JRE on windows

**TODO:**
* change the format of the profiles from binary to xml
* change the Ui to look better/different
* Make the applying of the effects in a background thread so that the gui doesnt freeze

**Release History**
v. 0.4b:
* Added support for M11x
* Added support for active preview
* Added support for Battery Monitoring
* Added support for brightness
* Added Turn off features
* Fixed Windows visual bugs

v. 0.3:
* Added support for copying/pasting a sequence of actions
* Added support for changing a lot of colors at once
* Added reset function
* Removed the info button and copy button

v. 0.2:
* Added support for 32 bit linux
* Added support for sequences
* Added support for copy/paste of action
* Added support for right click on color to select the color from an action
* Added support for "colors in profile"
* Added support for morph/blink
* Added support for speed
* Changed the Gui layout


**Screen Shots:**

[http://progger.co.uk/alienfx/linux.png](http://progger.co.uk/alienfx/linux.png)

System Tray:
[http://progger.co.uk/alienfx/tray.png](http://progger.co.uk/alienfx/tray.png)


**DOWNLOAD LINK:**
[Executable]("http://progger.co.uk/alienfx/AlienFXLite-0.4b.jar") 

**SOURCE LINK:**
[Source]("http://progger.co.uk/alienfx/source-0.3.tar.gz")

---

### Post by gliderdad79 on 2010-02-11
Just trying this on a m17x running 9.10 and get this error


```
/Desktop$ sudo java -jar AlienFXLite-0.1.jar
Exception in thread "AWT-EventQueue-0" java.lang.UnsatisfiedLinkError: /tmp/lib_libAlien.so.3452837222987380116.tmp: /tmp/lib_libAlien.so.3452837222987380116.tmp: wrong ELF class: ELFCLASS64 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1747)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1656)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at uk.co.progger.alienFXLite.led.LEDController.<clinit>(LEDController.java:7)
	at uk.co.progger.alienFXLite.led.AlienFXControllerFactory.getAlienFXDevice(AlienFXControllerFactory.java:21)
	at uk.co.progger.alienFXLite.alienfx.AlienFXEngine.<init>(AlienFXEngine.java:22)
	at uk.co.progger.alienFXLite.gui.MainFrame.<init>(MainFrame.java:56)
	at uk.co.progger.alienFXLite.Main$1.run(Main.java:23)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:602)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)

```

---

### Post by Wattos on 2010-02-12
> **gliderdad79 said:**
> Just trying this on a m17x running 9.10 and get this error


```
/Desktop$ sudo java -jar AlienFXLite-0.1.jar
Exception in thread "AWT-EventQueue-0" java.lang.UnsatisfiedLinkError: /tmp/lib_libAlien.so.3452837222987380116.tmp: /tmp/lib_libAlien.so.3452837222987380116.tmp: wrong ELF class: ELFCLASS64 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1747)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1656)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at uk.co.progger.alienFXLite.led.LEDController.<clinit>(LEDController.java:7)
	at uk.co.progger.alienFXLite.led.AlienFXControllerFactory.getAlienFXDevice(AlienFXControllerFactory.java:21)
	at uk.co.progger.alienFXLite.alienfx.AlienFXEngine.<init>(AlienFXEngine.java:22)
	at uk.co.progger.alienFXLite.gui.MainFrame.<init>(MainFrame.java:56)
	at uk.co.progger.alienFXLite.Main$1.run(Main.java:23)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:602)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)

```

It seems to me you are running 32-bit version of ubuntu? This release only supports the 64 bit release. The next release will have support for 32 bit.

---

### Post by Wattos on 2010-02-12
Version 0.2 is out! 

Unfortunately the profiles from 0.1 wont be read into 0.2. 

BUT: 

Now you can do sequences of actions, select colors from action (right click on an action), set the speed of the sequences, see all colors used in the profile (and select them), Add morphs and blinks. 

This tool is now almost as powerfull as the command center (and also adds some more features like copy/paste, insertion into any place on the sequence and you can CHANGE THE COLORS OF THE EYES of the powerbutton). 

Also, this version adds support for 32bit linux. 

Hope you like it. Next version will include a undo/redo functionality + revert changes to profile from last saved time and hopefully bugfixes.

Enjoy. Please leave some feedback on what you like and dont like.

---

### Post by HunterThomson on 2010-02-13
WOW :D

This is Amazing !
I didn't think you'd get the morph and flash working so fast.
Way COOL !

I am using Archlinux x86-64 and no problems at all on my Alienware M15x.

This is just a powerful as the one that Alienware Ships. Heck it is loads easier to make themes with too. I love it. Alienware laptops have been around for a long time but as far as I can tell this is the fist and only AlienFX manager that anyone has written outside of Alienware corporation and it works on Linux :)

Got to Love Open-source Development. Way faster and works way better every time.

:KS Keep up the good work :KS

Owe, hay could you post the C Modules/Classes/Libs... you know the C functions you are calling to do the work. I'd like to write one in Python-GTK. Not to steal your thunder but just because I need to practice programing and I don't like Java.

---

### Post by Wattos on 2010-02-15
> **HunterThomson said:**
> WOW :D

This is Amazing !
I didn't think you'd get the morph and flash working so fast.
Way COOL !

I am using Archlinux x86-64 and no problems at all on my Alienware M15x.

This is just a powerful as the one that Alienware Ships. Heck it is loads easier to make themes with too. I love it. Alienware laptops have been around for a long time but as far as I can tell this is the fist and only AlienFX manager that anyone has written outside of Alienware corporation and it works on Linux :)

Got to Love Open-source Development. Way faster and works way better every time.

:KS Keep up the good work :KS

Owe, hay could you post the C Modules/Classes/Libs... you know the C functions you are calling to do the work. I'd like to write one in Python-GTK. Not to steal your thunder but just because I need to practice programing and I don't like Java.


I will post the code on sourceforge as soon as I fix some issues with the amount of garbage the gui is generating. Should be up today

---

### Post by Vakman on 2010-02-15
Wow. I am impressed even.
Never seen anyone bother with this outside of Alienware either.
I was going to buy an Alienware but I opted for ASUS UL80-VT for the battery life.

---

### Post by gliderdad79 on 2010-02-16
> **Wattos said:**
> It seems to me you are running 32-bit version of ubuntu? This release only supports the 64 bit release. The next release will have support for 32 bit.

Yup, that was my mistake, I switched over after this post to 64 bit and just grabbed the new version. Working great on m17x 64 bit, Thank you!!

---

### Post by Wattos on 2010-02-16
Released another version. This will probably be the last version unless there are severe bugs or a high demand for some kind of functionality. 

Once I get someone to help me to add support for the M11x I will do that. 

In the 0.3 version expect the following changes:

*Now you can select multiple actions and then paste them.
  The selection has a SHIFT and CTRL modifier. If shift is pressed, you only add actions to the selection. If CTRL is pressed, you only remove actions from the selection.

*Pressing with the left mouse button on any color in the "used color panel" will change all actions with that color to the currently selected color

*Pressing with the right mouse button on any color (including the actions) will select that color

*you can now reset the lights in case something funny is happening. 

*a faster gui

---

### Post by HunterThomson on 2010-02-19
Hum, I am getting an unbearable problem with the new version of AlenFXLight.

When I set one thing to be Blue. Then one thing read. Then one thing blue agin. Then I select a new color everything that is that Blue color will get it's color changed too.

Dose my explanation make sens?

Big problem. I am not even using 0.3 anymore. I have to use the 0.2 version.

---

### Post by Wattos on 2010-02-19
> **HunterThomson said:**
> Hum, I am getting an unbearable problem with the new version of AlenFXLight.

When I set one thing to be Blue. Then one thing read. Then one thing blue agin. Then I select a new color everything that is that Blue color will get it's color changed too.

Dose my explanation make sens?

Big problem. I am not even using 0.3 anymore. I have to use the 0.2 version.

Im not sure I follow, but you actually might be talking about a feature I put in. The "Color Used panels" can be used in 2 different ways. _Right_ clicking on a color which choose that color as the currently selected color. Left  clicking on the button will make every instance of that color change to the selected one. This allows for quick color swapping. 

If this is not your problem, can you explain a little more? Can you maybe make a screenshot or two?

---

### Post by HunterThomson on 2010-02-19
OWE Okay.

Thanks, ya I was just left clicking everything. Ok, so now I am doing the whole right click to select and left click to change and it is all working as I want it to now.

---

### Post by tux_mark_5 on 2010-02-24
I have to say: superb application ;)
Who would have imagined that linux will receive the best of AlienFX.

Everything seems to work quite nicely, however:
When I should down my computer (and leave it for a while, like 1 day) and when I plug in the power, no lights turn on. When I turn it on, all zones start flashing. It seems that there is something not right with saving config to EEPROM.

I have Alienware M17x.

---

### Post by Wattos on 2010-02-27
> **tux_mark_5 said:**
> I have to say: superb application ;)
Who would have imagined that linux will receive the best of AlienFX.

Everything seems to work quite nicely, however:
When I should down my computer (and leave it for a while, like 1 day) and when I plug in the power, no lights turn on. When I turn it on, all zones start flashing. It seems that there is something not right with saving config to EEPROM.

I have Alienware M17x.

Well, that doesnt sound right. So there are 2 possible solutions for it. Either, I disable saving to EEPROM, which would fix that issue, but then you would have to reset the lights everytime you boot into the OS, or you can help me find the issue. I dont have an M17X, so the following would have to be done:

On Windows:
Install USBSniff: [http://www.pcausa.com/Utilities/UsbSnoop/](http://www.pcausa.com/Utilities/UsbSnoop/)
Select the device with Vendor Id 187c and PId 512
Then install the sniffer there.
Restart the laptop.
Now press Fn + F11 to turn of the lights
Now start USBSniff make sure to pause->close->delete the logfile
Resume logging
Press Fn+F11
wait a wee bit until the light turn up
press on pause->close
and post the logfile here. That way I can exactly see what Command Centre sends on the M17X and fix stuff :)

---

### Post by tux_mark_5 on 2010-02-27
I did what you said.
I have created two logs:
UsbSnoop0.log - all zones have same color
UsbSnoop1.log - keyboard 4/numpad is morphing, the rest - have single color

I've created 2 instead of 1 log, because I've noticed that when I set all zones to morph, after complete shutdown and when powering laptop on everything starts flashing.
In contrast to this, when setting all colors to "plain color" in AlienFX lite, usually after restart the theme is either:
a) retained
b) everything is just black

So it seems that problems are a bit more related to morphing + saving.
Feel free to ask anything else that might help resolve this issue.

---

### Post by jebinem1999 on 2010-03-01
Any chance we could get this for the new m11x? I have one and am willing to help.

BTW, excellent work!

---

### Post by aosmith on 2010-03-04
Dude this is fantastic works great with my m17x as well... more customization than stock software THANKS!

---

### Post by Wattos on 2010-03-05
> **tux_mark_5 said:**
> I did what you said.
I have created two logs:
UsbSnoop0.log - all zones have same color
UsbSnoop1.log - keyboard 4/numpad is morphing, the rest - have single color

I've created 2 instead of 1 log, because I've noticed that when I set all zones to morph, after complete shutdown and when powering laptop on everything starts flashing.
In contrast to this, when setting all colors to "plain color" in AlienFX lite, usually after restart the theme is either:
a) retained
b) everything is just black

So it seems that problems are a bit more related to morphing + saving.
Feel free to ask anything else that might help resolve this issue.

Thanks, just a question, which command centre do you have installed? Was it the A05?

> **jebinem1999 said:**
> Any chance we could get this for the new m11x? I have one and am willing to help.

BTW, excellent work!

Yes, I got someone to help me test. It should be out next week among with some more options. Are there any wishes for features?

---

### Post by tux_mark_5 on 2010-03-08
I think that it is A05.
I've updated all software from dell's site a while ago.

---

### Post by Wattos on 2010-03-10
> **tux_mark_5 said:**
> I think that it is A05.
I've updated all software from dell's site a while ago.

AO5 is buggy. You would have to revert to AO3 or AO4. It causes weird behaviour most of the time.

---

### Post by tux_mark_5 on 2010-03-10
> **Wattos said:**
> AO5 is buggy. You would have to revert to AO3 or AO4. It causes weird behaviour most of the time.

Well, it's not a problem for me anymore.
I've written small app in C++, which allows me to configure the lights just the way I can in AlienFX/AlienFX Lite (with saving to EEPROM disabled). It's console/text based and therefore I can now script various system events to reflect on my M17x ;)

---

### Post by Wattos on 2010-03-11
> **tux_mark_5 said:**
> Well, it's not a problem for me anymore.
I've written small app in C++, which allows me to configure the lights just the way I can in AlienFX/AlienFX Lite (with saving to EEPROM disabled). It's console/text based and therefore I can now script various system events to reflect on my M17x ;)

you should share :)

---

### Post by tux_mark_5 on 2010-03-11
I will :)
Just have to smoothen few rough edges.
And to make it compatible with other alienfx devices.

---

### Post by Wattos on 2010-03-15
Finally, I finished the beta version of the next release. It now has support for the M11x. I call this version "Beta" as there are some new features which I did test but might have bugs.

Also, remember, if the AlienFX seems to be stuck, then do:

Turn off pc
unplug all cables + battery
hold power button for 10 seconds
start pc normally

Please leave some feedback :). 

Here is a video tutorial on how to use the app:

[http://www.youtube.com/watch?v=3SPJAFx5Meo](http://www.youtube.com/watch?v=3SPJAFx5Meo)

---

### Post by danilius on 2010-03-22
I downloaded version 0.4 onto my 32-bit Ubuntu Alienware Mx15, and attempted to run it, but got the following error:

```
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
    at uk.co.progger.alienFXLite.gui.MainFrame.updateTray(MainFrame.java:225)
    at uk.co.progger.alienFXLite.gui.MainFrame.<init>(MainFrame.java:135)
    at uk.co.progger.alienFXLite.Main$1.run(Main.java:27)
    at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
    at java.awt.EventQueue.dispatchEvent(EventQueue.java:602)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
    at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
    at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)
```Have I downloaded the wrong version? Where can I get the correct one?

Judging by what I saw on Youtube, this is a seriously cool piece of code. Kudos to you!

---

### Post by tahnok on 2010-03-23
This is f**king sweet! Thanks for letting me enable and disable lighting effects while in linux! This works flawlessly on my m11x

---

### Post by HunterThomson on 2010-03-25
> **tux_mark_5 said:**
> Well, it's not a problem for me anymore.
I've written small app in C++, which allows me to configure the lights just the way I can in AlienFX/AlienFX Lite (with saving to EEPROM disabled). It's console/text based and therefore I can now script various system events to reflect on my M17x ;)

Ya man, I want try your utility. I don't like Java and would love to script it.

----

Wattos: ya, I have some problem too. If I save my complex AlienFX setup with rainbow keyboard and rainbow alienhead. When I poweroff and then power back on a few mins latter the only lights that work are the keyboard and then left speaker light comes on for the fist few secs and then turns off.

If I set all the lights to be red. Then when I power on all the lights work except for the power button light.

----

If I could get that C++ scriptable utility from tux_mark_5 I would just put that in my startup script and all would be fine.

It would also be easier for me to know that is going on to just read your C++ application. Then I mite get more motivated to go ahead and write the pyGTK app.

---

### Post by tux_mark_5 on 2010-03-26
I had no time last week to finish the application, but now i have.
Mine approach to changing lights is to manually apply various effects. I mean: AlienFX has 3 built-in "effects": static color, morphing and blinking. Also there is no way to change the animation of a single zone. So that's why I'm using server-like approach, which calculates the color of each zone separately and sends it to the AlienFX controller using "static color" method.
This allows to create more advanced animations with varying speeds, ability to temporary interrupt the animation and so on.
Right now I am integrating libguile for configuration/animation creation/etc.

---

### Post by HunterThomson on 2010-03-29
> **tux_mark_5 said:**
> I had no time last week to finish the application, but now i have.
Mine approach to changing lights is to manually apply various effects. I mean: AlienFX has 3 built-in "effects": static color, morphing and blinking. Also there is no way to change the animation of a single zone. So that's why I'm using server-like approach, which calculates the color of each zone separately and sends it to the AlienFX controller using "static color" method.
This allows to create more advanced animations with varying speeds, ability to temporary interrupt the animation and so on.
Right now I am integrating libguile for configuration/animation creation/etc.

Hay that sounds fantastic. I'd really like to have your code.

---

### Post by N.Vector on 2010-03-30
Good Morning.

I am running an older Alienware M15x of the Ripley model design. I love this laptop dearly and it has treated me well. Up untill recently I had no problems with AlienFX. Now however the keyboard and touchpad flash random colors all the time. I can fix this when booting into windows, but once I reboot, it starts flashing again. This is incredibly annoying and I would suffice to just have the system darkened while in linux. 

I have tried your program in Windows and Linux Mint 8. Within windows it functions without a hitch. Under Linux Mint however it freezes once I launch. Any recommendations on resolving this? I have already turned the laptop off with removed all attached devices and battery. 

I'm thinking this is more a problem with my board or with the firmware. as nothing seems to be saving to the eeprom.

---

### Post by tgilbert328 on 2010-04-20
Hi guys,

I have ubuntu 9.10 64 running on m15x.  I am getting a similar exception as above:

```

Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
	at uk.co.progger.alienFXLite.gui.MainFrame.updateTray(MainFrame.java:225)
	at uk.co.progger.alienFXLite.gui.MainFrame.<init>(MainFrame.java:135)
	at uk.co.progger.alienFXLite.Main$1.run(Main.java:27)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:602)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)

```

It seems to be crashing when it tries to update the system tray.  Its seems relevant that when the application starts up it warns me that it can't find the system tray and will not run in the background.

Looking at the code, its how the exception is caught when it can't setup the system tray, so I assume there is a problem in there somewhere...

I write some Java EE, but never swing.  How can I debug this program if it has to run as admin?

Tim

---

### Post by georgestan on 2010-04-24
Hi Watoos,

I am using 0.4b with m15x and having a problem here. The first time I run it on Ubuntu 9.10 64, I created a profile and applied it. However, when I later want to alter it, the GUI freezes when I clicked apply (forever until I killed it). Later when I tried to run the app again, it freezes even when loading my profile. 

I tried earlier versions, all of which could load the profile but freezed when I apply the new profile.

Now I just want to restore what it was. I use the Dell alienfx tool on Windows, but regardless of whatever I choose and apply, turn on and turn off, the lighting effect does not change at all.

[Updated]
Well, I got it back to the original state by shutting down the laptop for half an hour and restart. The original lightings are back.

---

### Post by nihilum on 2010-04-25
> **tgilbert328 said:**
> Hi guys,

I have ubuntu 9.10 64 running on m15x.  I am getting a similar exception as above:

```

Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
    at uk.co.progger.alienFXLite.gui.MainFrame.updateTray(MainFrame.java:225)
    at uk.co.progger.alienFXLite.gui.MainFrame.<init>(MainFrame.java:135)
    at uk.co.progger.alienFXLite.Main$1.run(Main.java:27)
    at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
    at java.awt.EventQueue.dispatchEvent(EventQueue.java:602)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
    at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
    at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)

```It seems to be crashing when it tries to update the system tray.  Its seems relevant that when the application starts up it warns me that it can't find the system tray and will not run in the background.

Looking at the code, its how the exception is caught when it can't setup the system tray, so I assume there is a problem in there somewhere...

I write some Java EE, but never swing.  How can I debug this program if it has to run as admin?

Tim

running ubuntu 9.10 x64 on m11x and getting the same error

---

### Post by StormRoBoT2 on 2010-04-29
will this work on ubuntu 10.04 64bit?

using M15X with core i7

---

### Post by [Neurotic] on 2010-05-02
Just started playing with this! This is awesome :D Nice one!

---

### Post by HunterThomson on 2010-05-03
boy, This is broken in Arch Linux.

It broke a while back... owe 4 weeks, I was just to busy to say anything. It was after some updates that had nothing to do with Java or anything that should have caused a problem. I even rolled back all the upgraded packages but still no luck.

At first it was saying that it found the device but could not communicate with it and then would lock up.

Then I put in the old HHD with windows on it and set the colors to all sold blue.

Now I get a diffrent error. It now tells me...

"Your system seems not to support systems trays. This application will not run in the background."

Then it shows the application window but is frozen and I have to kill from the shell. 

---------------------

OS - Arch Linux x86_64
Kernel - 2.6.33
Alienware M15X - Core i7-720QM

I have tried both the closed JRE "That use to work fine" and I also installed the "OpenJDK". Same problem in both.
---------------------

Ya, see this is why I don't like JAVA. The UI doesn't match the rest of my desktop, It's a pain in the *** to code, and it just doesn't work that well. Arg...

I finally found the motivation to write a Python utility but I'm busy with school right now finals and all. Would be super cool if I could get the C++ code that way I will not have to dig through he Java to find it.

---

### Post by Philip550c on 2010-05-26
Im using this program and it is working quite well with my m11x, except that the right and left speakers are reversed. I didnt read through the entire thread so forgive me if this has been stated before but how can i make a launcher for it so that i have an icon in my startmenu?

---

### Post by night reveller on 2010-06-03
Works great on my m11x. Thanks for sharing this.

---

### Post by ThomasB2k on 2010-08-05
I am trying this on my Alienware m15x (Purchased in August 2008 ) and it says "Error communicating with alienfx device: Data length should be 9 but was -4"

---

### Post by ThomasB2k on 2010-09-11
bump, sorry

---

### Post by adk46er on 2010-09-11
I have AlienFXLite-0.4b.jar set to run with Java 6 runtime, but when I double click I get the error message:

The application was unable to communicate with the alienFX device. The device is either not present, or the application lacks sufficient rights to access the device.

I've been forum surfing for a solution but no luck so far. Any tips are appreciated.

**EDIT**   Solved! I had it in the wrong directory <sheepish smile>

Very cool-- works great!! Impressive that you can do what the creators of the machine cannot....

---

### Post by rockingthe2 on 2010-09-28
I have an Alineware M15x running ubuntu 10.04, downloaded the program and placed it in the documents folder. checked that i have all the required software, getting error message: Unable to access jarfile AlienFXLite-0.1.jar. am I doing something wrong? I typed in what you have on the first post to type in. please help i'm kinda new to ubuntu and am still trying to figure this out. thanks

---

### Post by gshearer on 2010-10-04
Has anyone gotten around to writing a command line tool for this yet? I saw some talk of this, but can't find anything.

I'd like to be able to script system events to Alien FX.

---

### Post by chargersfan420 on 2010-10-08
I just want to say a big THANK YOU to Wattos for putting together this amazing program!  It works better than Alienware's AlienFX for programming patterns.

For feature ideas, all I can think of at the moment would be to make the tray icon have a transparent background, and maybe some sort of option in the program to have the tray icon launch on startup.

Keep up the good work!

---

### Post by gliderdad79 on 2010-10-08
This is working running ubuntu 10.10 64 m17x

---

### Post by HunterThomson on 2010-10-09
> **adk46er said:**
> I have AlienFXLite-0.4b.jar set to run with Java 6 runtime, but when I double click I get the error message:

The application was unable to communicate with the alienFX device. The device is either not present, or the application lacks sufficient rights to access the device.

I've been forum surfing for a solution but no luck so far. Any tips are appreciated.

**EDIT**   Solved! I had it in the wrong directory <sheepish smile>

Very cool-- works great!! Impressive that you can do what the creators of the machine cannot....

I had the same problem. But it fixed it self when I put in the hard drive that came with it and booted into windows. I think windows program for it fixed it. This was easy for me because I just took out the hard drive and put in an SSD and installed Linux on it, so I still had the windows hhd.

Ya, man I want that C code to make a command line or scripted inter action with the AlienFX. GUI's are problematic in the long run with out constant development.

---

### Post by chargersfan420 on 2010-10-09
Nevermind about the transparent tray icon.  I was launching it with sudo since I didn't have USB permissions, but once I solved that problem it is transparent now.

I can't seem to find a way to get it to automatically launch on startup (the tray icon, that is).  Anyone come up with a good method?  It seems necessary since once in a while when I boot, only half of the keyboard lights up and nothing else until I've activated the tray icon.  This is true for both Ubuntu and Win7.

---

### Post by kvonb on 2010-10-28
Well done Wattos, I found your app in a google search and installed it under both PCLinuxOS 2010 and Windows7 on my Alienware m17x.

It works perfectly, and even better than the original Dell bloatware version.  It can do things they can't, I especially like that I can make the power button "Alien Head" black, and the eyes (HDD LED) red.  It looks good, and also makes it much easier to see the HDD LED!

A good friend of mine is working on a native Linux version but is having difficulties, would it be possible for him to ask you a few questions about the low level programming techniques you used?

Again, thanks a million :).

---

### Post by Philip550c on 2010-11-23
Thanks for making this program. I love it on my m11x but I cannot change the color of the ring around the alienhead power button. It stays blue no matter what I do, even if all the other lights are off the ring is still on blue unless i unplug the power than it is yellow

---

### Post by hitokiri_jaguar on 2010-11-26
:grin: thanks a lot man, really cool app, something that is really needed by Alienware PC owners

---

### Post by rlapa on 2011-01-03
Can't make it work on a Alienware m15x (Bios vX36 P3 (08/29/2008) )

Error occured while trying to communicate with the AlienFX device: Data length should be 9 but was -4.

Can I help you help me? ;)

lsusb -v
> 
Bus 006 Device 005: ID 187c:0511  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x187c 
  idProduct          0x0511 
  bcdDevice            1.00
  iManufacturer           1 Alienware
  iProduct                2 AlienFX Mobile
  iSerial                 3 1.00.35
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              1 Alienware
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0001
  Self Powered


---

### Post by heiserhorn on 2011-01-08
Thanks Man,
Awesom app. Works grate on my 15x with ubuntu 10.10.

cheers

---

### Post by callmemister on 2011-01-13
Hi, I've tried to make it work, but nope, no luck.

''I follow the instructions, and I get this The application was unable to communicate with alienFX Device. The device is either noet present, or the application lacks sufficient rights to access the device.'' As a pop-up msg. and get this in the terminal if I try ''java -jar ~/AlienFX/AlienFXLite-0.4b.jar''

____________ java -jar ~/AlienFX/AlienFXLite-0.4b.jar
libusb couldn't open USB device /dev/bus/usb/002/003: Permission denied.
libusb requires write access to USB device nodes.


I'm not a Pro in Linux, but I try to learn. Any detailed explanation would be appreciated. :confused:

---

### Post by chargersfan420 on 2011-01-14
Hey callmemister, here is how I got USB permissions working properly in Ubuntu 10.10 (Maverick) (for use with AlienFXLite):

(Keep in mind there are several ways to get this done, this is just one method!)

First, go to System - Administration - Users and Groups.  Click on the "Manage Groups" button.
If you don't have one already, create a group called "usbusers".  After you create it, highlight it and click on Properties.  Put a checkmark next to your name (and anyone else who needs full permissions to USB devices).

Then open up a terminal (Applications - Accessories - Terminal).
In the terminal, type:
```
sudo gedit /etc/udev/rules.d/47-usb.rules
```
This should open up an empty file in a text editor called "gedit".
(note that the name of the file is not important, you can call it whatever you want, but since the rules in this folder are executed in order, I think it is best to name it starting with a number in the 40-49 range)

In that file, write the following:
```

# User Edit 
SUBSYSTEM=="usb", MODE="0666", GROUP="usbusers"

```
Save and close the file.  This file should allow full access (mode=0666) to anyone in the "usbusers" group for USB devices.  Also, the "# User Edit" is a comment (denoted by the # at the start of the line).  I like to leave comments in any file I edit just so I know I have been there before in case I come back to do more editing.

This next part I tried when stuff wasn't working so I'm not sure if it is necessary or not... back in the terminal, type:
```
sudo chmod a+rx /etc/udev/rules.d/47-usb.rules
```
(this makes the file you just created executable)

Reboot and cross your fingers!

---

### Post by tacobff on 2011-01-15
Would this work on Ubuntu netbook edition?
On a side note would the netbook edition be good for an m11x or the desktop edition?

---

### Post by callmemister on 2011-02-03
It works ! Thank you !!! Hope it helps more people

---

### Post by callmemister on 2011-02-18
> **tacobff said:**
> Would this work on Ubuntu netbook edition?
On a side note would the netbook edition be good for an m11x or the desktop edition?


It works fine.
Alltho if you install the 10.10 Netbook, I suggest System -> Admin -> Login Screen -> and select Ubuntu Desktop Edition, as the Netbook edition is not really usefull especially with the M11x.
And DO NOT install the Nvidia Drivers.

---

### Post by Biciclettapc on 2011-03-13
Is there a way to turn it off on battery?

Paul

---

### Post by JCrue on 2011-03-16
I'm getting the "The application was unable to communicate with the alienFX device. The device is either not present, or the application lacks sufficient rights to access the device" message too. Now, it does rather seem to have said rights, and I'm looking at the device now, so... :P

I'm an area 51 m15x and 10.04. If anyone can offer any help, it would be much appreciated.

---

### Post by yugo4k on 2011-05-06
I had the same problem as the guy above...

"AlienFX error
Error occured while trying to communicate with the AlienFX device: Data length should be 9 but was -4"

Any ideas?
Or how can I learn how to make my own light changing program/script? :D

I use a M15x, intel core2duo, ubuntu 10.04, 64bits.

---

### Post by chargersfan420 on 2011-05-06
JCrue that's the message you get when you don't have USB permissions.  Follow my instructions from post #54 and you should be okay.

yugo4k, I'm pretty sure I've seen that once before but I don't remember why... It might be a USB permissions issue, perhaps post #54 can help you too.

---

### Post by Gryphyn on 2011-05-14
Hey guys,
 
One thing I've been looking for is a program that will randomly select a different AlienFX color every time it runs, or at random time intervals.  Haven't found one. Anybody know of one?
 
Running Windows 7.

---

### Post by stewiefet on 2011-05-19
Wattos, excellent work sir.   Did you ever hear from tux_mark_5 about that C++/scripted version?  I think having the AlienFX lights change to reflect system status/events or new mail/IM messages would be awesome..

---

### Post by nutsy.ben on 2011-05-26
> **adk46er said:**
> I have AlienFXLite-0.4b.jar set to run with Java 6 runtime, but when I double click I get the error message:

The application was unable to communicate with the alienFX device. The device is either not present, or the application lacks sufficient rights to access the device.

I've been forum surfing for a solution but no luck so far. Any tips are appreciated.

**EDIT**   Solved! I had it in the wrong directory <sheepish smile>

Very cool-- works great!! Impressive that you can do what the creators of the machine cannot....


Same problem, I did not see that there was a directory where it needs to be put.
Can someome detail a bit more the protocol, there is a step missing between 'download the executable' and 'run the command line'



Thanks

---

### Post by nutsy.ben on 2011-05-26
By the way, the post #54 did not work for me.

---

### Post by yugo4k on 2011-05-26
> **chargersfan420 said:**
> JCrue that's the message you get when you don't have USB permissions.  Follow my instructions from post #54 and you should be okay.

yugo4k, I'm pretty sure I've seen that once before but I don't remember why... It might be a USB permissions issue, perhaps post #54 can help you too.

Thanks for the tip chargersfan420, I followed that but it still gives the same "Data length should be 9 but was -4" output... :(

---

### Post by eboyle12 on 2011-07-02
Just downloaded 11.04 the other day and still getting used to it.  I downloaded the file and followed the other steps but when i tried to access the file the terminal returned unavailable.  do i need to place the file in a specific directory?

---

### Post by Xqua on 2011-10-06
Hello,

I'm on a Alienware m11x R3, 

here's mu lsusb : 

```
Bus 002 Device 003: ID 413c:2107 Dell Computer Corp. 
Bus 002 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse (M-BT58)
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 187c:0522 Alienware Corporation 
Bus 001 Device 003: ID 0c45:6430 Microdia 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

So interesting line : 

Bus 001 Device 004: ID 187c:0522 Alienware Corporation 

And I've got the : 

The application was unable to communicate with the alienFX device. The device is either not present, or the application lacks sufficient rights to access the device.

I read that the R3 didn't work because of a change in the USB port f the lights ! 
Is it true ?

EDIT : 
I tried the #54, but didn't work, which does not surprised me as I tried in root before !

---

### Post by jocefus on 2011-10-18
I have same results as Xqua with my m14x

---

### Post by Xqua on 2011-10-19
Sadly this is Java and I don't know **** about Java ...

Otherwise I would have tried to look at the code !
I read somewhere that the USB controler changed a little bit, does anyone with Java knowledge could take a look if the USB Adress is Hard Coded inside ? 
In that case a small patch would work !

---

### Post by Dark Ghost on 2012-06-08
I really want to use ubuntu on my alienware m14x but this driver is quite old. Anyone got it to work yet? or have an alternative way of activating alienfx and disabling it?

---

### Post by Xqua on 2012-06-09
Hey ! 

I wrote a new driver in python as this one did not worked !

It should worked with your M14x !!

it is called pyAlienFX : code.google.com/p/pyalienfx/

Enjoy !

---

### Post by Dark Ghost on 2012-06-09
Thank you very much sir. Been looking for this for a while :). I'm really interested in the code. Thank you very much again

---

### Post by mpz on 2012-10-31
Did not install on my archlinux powered m18x
```

[user@alien pyalienfx]$ python --version
Python 3.2.3
[user@alien pyalienfx]$ sudo ./install.py 
  File "./install.py", line 29
    You are about to instal the software : pyAlienFX !"""
                                                        ^
SyntaxError: invalid syntax

```

I appreciate the efforts though.

---

### Post by Xqua on 2012-11-01
Hello ! 

Can you use python 2.7 instead and tell me if it works ? 

Otherwise you can start the soft just by typing 

sudo ./pyAlienFX.py 

It will work just the same especially because the install script is mainly for ubuntu purposes ! (There is someone working on making a ArchLinux package )

---

### Post by Dabo Ross on 2012-12-11
Would this work with the mx14? I installed Ubuntu a while ago, just now using it. I would like to be able to update my keyboard in Ubuntu. I have heard that certain things can ruin the controls, so I am hesitant to try it.
EDIT: I think you already answered my question :P. I hadn't really read the replies before.

---

### Post by Dabo Ross on 2012-12-11
When I click the download link, I get this... "Oops! Google Chrome could not find progger.co.uk"
EDIT: Sorry for double post, I thought someone else had posted after I had.

---

### Post by Xqua on 2012-12-12
Bonjour,

Telecharger le ici : 

[http://code.google.com/p/pyalienfx/](http://code.google.com/p/pyalienfx/)

pour ubuntu 12.04 et superieur : 

[http://code.google.com/p/pyalienfx/downloads/detail?name=pyalienfx_1.0.2_all.deb&can=2&q=](http://code.google.com/p/pyalienfx/downloads/detail?name=pyalienfx_1.0.2_all.deb&can=2&q=)

Sinon : 

[http://code.google.com/p/pyalienfx/downloads/detail?name=pyAlienFX-latest.tar.gz&can=2&q=](http://code.google.com/p/pyalienfx/downloads/detail?name=pyAlienFX-latest.tar.gz&can=2&q=)

Aussi :
> **mpz said:**
> Did not install on my archlinux powered m18x
```

[user@alien pyalienfx]$ python --version
Python 3.2.3
[user@alien pyalienfx]$ sudo ./install.py 
  File "./install.py", line 29
    You are about to instal the software : pyAlienFX !"""
                                                        ^
SyntaxError: invalid syntax

```I appreciate the efforts though.

Le packet Arch est sorti !

---

### Post by xblx on 2013-01-02
Hi,

I was wondering if this could be made to work on an Alienware X51. Tried to look for a USB device, but nothing looks like the hardware lights:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04ca:0027 Lite-On Technology Corp. 
Bus 001 Device 004: ID 0461:4d65 Primax Electronics, Ltd 
```

Any idea how to look for the device?

---

### Post by Xqua on 2013-01-03
Hi

It seem to be a totally different technology that is used here ...

normally you should see something like : 

Bus 001 Device 005: ID 187c:0522 Alienware Corporation 

OR at least some device by the vendor tag : 187c

... I'm not sure it would be easy to adapt it to that model ...

But if you can gather more information on how does the lights works ?

---

### Post by mmpisoni on 2013-01-05
Hi Xqua,

I've installed pyAlienFX on Arch Linux (running Gnome) and am having issues I was hoping you could help with.

1) When I open pyAlienFX from the terminal, the UI opens up as a very wide window, almost 2x the width of my monitor.  This isn't too big of a deal because I can still work with it, just wondering if it's a problem on my end.  Also at start I see the following in the terminal output:
[B]
(gksu:7094): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(pyAlienFX.py:7105): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",[/B]

Initializing Driver  ...
Comnputer M14XR1 found ! Loading the parameters ...
Initializing Controller ...
[B]the Deamon is disconnected ... 
Trying to load the driver manually[/B]
Loading : ./Profiles/2013.cfg
SPEED =  65280
Initializing Interface ...
**/opt/pyAlienFX/pyAlienFX.py:123: GtkWarning: Can't pass in construct-only parameters to cancel_button**
  self.gtk_AlienFX_Main.add_from_file('./glade/AlienFXMain.glade')
**/opt/pyAlienFX/pyAlienFX.py:123: GtkWarning: Can't pass in construct-only parameters to ok_button**
  self.gtk_AlienFX_Main.add_from_file('./glade/AlienFXMain.glade')


Would the bolded messages be preventing functionality?

2.) The program just doesn't seem to be doing what it's supposed to.  I can kind of change colors in the UI, but clicking Save or "Lights On" from the menu doesn't do anything (produces a USB related error in the console):

.Sending : Get Status
Packet :  02 06 00 00 00 00 00 00 00
array('B', [16, 0, 0, 0, 0, 0, 0, 0])
Sending : Reset All Lights On
Packet :  02 07 04 00 00 00 00 00 00
Traceback (most recent call last):
  File "/opt/pyAlienFX/pyAlienFX.py", line 940, in on_Save_pressed
    self.Set_Conf(Save=True)
  File "/opt/pyAlienFX/pyAlienFX.py", line 710, in Set_Conf
    self.controller.Write_Conf()
  File "/opt/pyAlienFX/AlienFX/AlienFXEngine.py", line 161, in Write_Conf
    self.WaitForOk()
  File "/opt/pyAlienFX/AlienFX/AlienFXEngine.py", line 269, in WaitForOk
    while not self.Get_State():
  File "/opt/pyAlienFX/AlienFX/AlienFXEngine.py", line 277, in Get_State
    self.driver.Take_over()
  File "/opt/pyAlienFX/AlienFX/AlienFXEngine.py", line 109, in Take_over
    self.dev.detach_kernel_driver(0)
  File "/opt/pyAlienFX/usb/core.py", line 695, in detach_kernel_driver
    self._ctx.backend.detach_kernel_driver(self._ctx.handle, interface)
  File "/opt/pyAlienFX/usb/_debug.py", line 52, in do_trace
    return f(*args, **named_args)
  File "/opt/pyAlienFX/usb/backend/libusb10.py", line 565, in detach_kernel_driver
    _check(_lib.libusb_detach_kernel_driver(dev_handle, intf))
  File "/opt/pyAlienFX/usb/backend/libusb10.py", line 357, in _check
    raise USBError(_str_error[retval.value])
**usb.core.USBError: Entity not found**

The output of lsusb:
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
[B]Bus 003 Device 004: ID 187c:0521 Alienware Corporation 
[/B]
I guess my assumption is all the problems are related to it not being able to connect properly to the device.  Please let me know if you have any suggestions.  Thanks in advance!

-m

---

### Post by Xqua on 2013-01-07
Hi,

That issue is known and I have to create a package for Arch Linux user specifically !

Meanwhile you can follolw the instructions here : 

[http://code.google.com/p/pyalienfx/issues/detail?id=8](http://code.google.com/p/pyalienfx/issues/detail?id=8)

- copy libusb-1.0.so.0 from an ubuntu installation (/lib/x86_64-linux-gnu on my ubuntu installation) - in root, I have launched : LD_PRELOAD=/path/to/copy/of/ubuntu/lib/libusb-1.0.so.0 pyAlienFX


Thanks for using pyAlienFX ;)

---

### Post by jardineworks on 2013-01-27
Hey Guys,

I am trying to get this working on my M17x R4 but when I launch the pyAlienFX app I get the following --

Initializing Driver  ...
Comnputer M17XR3 found ! Loading the parameters ...
Initializing Controller ...
the Deamon is disconnected ... 
Trying to load the driver manually
Loading : ./Profiles/Default.cfg
SPEED =  65280
Check Deamon
Check Deamon

I tried running the app with -h, --help etc but it doesn't seem to be implemented. Can someone tell me how to solve this issue?

---

### Post by Dabo Ross on 2013-01-27
I never got pyAlienFx to work on my mx14, but I don't really need it as I really do like it just staying as the light blue.

---

### Post by jardineworks on 2013-01-28
I like the blue as well, but it'd be nice to be able to turn some of the bling off sometimes :). 

Can someone tell me what Daemon it is trying to start? I can see another shell script in the pyAlienFX directory that references the daemon but I am hesitant to try to run it -- I'm worried that I might bugger something up.

---

### Post by jardineworks on 2013-01-28
Ok -- I figured what the hell. I ran the daemon script and it looks like it is running. I then run pyAlienFX and it prompts me for my root password. I entered it, but I don't see anything else. No errors, no GUI nadda.

---

### Post by jardineworks on 2013-01-28
Ok -- last hint for anyone following this thread. Daemon is running without issue, I can seend Ping -> Pong request responses. When I run the pyAlienFX_Launcher in a separate terminal window (as sudo) I see this output --

Initializing Driver  ...
Comnputer M17XR3 found ! Loading the parameters ...
Initializing Controller ...
Loading : ./Profiles/Default.cfg
SPEED =  65280
Check Deamon
Sending Ping
Sent ...
Traceback (most recent call last):
  File "./pyAlienFX_Indicator.py", line 130, in <module>
    indicator.main()
  File "./pyAlienFX_Indicator.py", line 107, in main
    self.check_daemon()
  File "./pyAlienFX_Indicator.py", line 114, in check_daemon
    ping = self.gui.controller.Ping()
  File "/usr/share/pyAlienFX/pyAlienFX.py", line 1269, in Ping
    pong = self.getResults()
  File "/usr/share/pyAlienFX/pyAlienFX.py", line 1194, in getResults
    data = self.sock.recv(self.BUFSIZE)
socket.timeout: timed out


Does anyone know how to get around this? I'm not sure why the socket is timing out since I can see the communication between to the two terminal sessions happening.

---

### Post by Xqua on 2013-01-30
Hi !

I'm the Developper ;) 


If you are running under Ubuntu : 
Can you try to download the last DEB file on the main page ? 
And then remove all the files you already have on your machine, then follow the install instruction on the Wiki of the main site. 
[http://code.google.com/p/pyalienfx/](http://code.google.com/p/pyalienfx/)

If it still doesn't work can you post an Issue on the main site with the whole Traceback etc ! ;) 

Thanks :D

---

