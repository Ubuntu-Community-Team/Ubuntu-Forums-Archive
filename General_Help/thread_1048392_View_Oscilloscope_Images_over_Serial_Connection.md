---
title: "View Oscilloscope Images over Serial Connection"
date: 2009-01-23
forum: General Help
---

### Post by MaindotC on 2009-01-23
Is there a program that will take images from an oscilloscope that I have connected via serial port?

---

### Post by ieee488 on 2009-01-23
Oscilloscopes and other instruments generally communicate via the IEEE-488 bus. Some instruments are capable of communication via RS-232 port.

How did you accomplish this task in Windows?

---

### Post by MaindotC on 2009-01-23
The program our instructor wants us to use is called Waveform Lite for the Tektronix TDS210.  Apparently it takes the output from the oscope and puts it in the Waveform Lite program so you can take a screenshot.  If there's any program that does that that runs natively my professor said that's perfectly fine.

---

### Post by ieee488 on 2009-01-23
I don't know of a Linux equivalent, but that doesn't mean there isn't one.

Basically, you would need to get the Programmers Manual from Tektronix's website, and read-up on how to send commands to the scope and how to read the data the scope sends back. To make sure the handshake is working, use minicom to send *IDN?.

---

### Post by MaindotC on 2009-01-23
Yeah I'm familiar w/ Minicom because I've console'd into switches and routers before but I need the oscilloscope reading - the wavy lines on the green screen - to appear on my machine so I can take a screenshot of it.

---

### Post by HyperHacker on 2009-01-23
I assume you've tried running that in Wine?

---

### Post by MaindotC on 2009-01-23
Yes I have - there are some issues that I know I can fix but I'm not certain I'll be able to get it to interact w/ the serial port as it should.  In the meantime I was hoping there were some native apps that may do the trick.

---

### Post by ieee488 on 2009-01-23
> **strAlan said:**
> Yeah I'm familiar w/ Minicom because I've console'd into switches and routers before but I need the oscilloscope reading - the wavy lines on the green screen - to appear on my machine so I can take a screenshot of it.

I understand what you want to do. My job is writing software to control test equipment, among them scopes.

Acquiring data from the scope is NOT a trivial task.

minicom is just to make sure you have the handshaking correct and can communicate in Linux

After that, you'll need to either use C, BASIC, or whatever language to send commands to and receive data from the scope via RS-232.

---

### Post by Entropy512 on 2010-01-05
I have found that Perl works quite well for test equipment interfacing.

Jeff Mock's GPIB library ( [http://www.mock.com/gpib/](http://www.mock.com/gpib/) ) hasn't been updated in years, however the basics are still there.  You'll probably need to modify it a little to support serial instead of GPIB.  (Last I checked it didn't support direct serial to test equipment), and then implement a class to control your test equipment.

Long ago I added support for a bunch of pieces of test equipment to that library (but never re-released my code), it wasn't very difficult at all.  I had methods in each instrument class that could retrieve a trace from the scope and return a Perl array.  Once you've got a Perl array you can use something like GD to plot it.  I'll likely be doing just that soon for the Rigol DS1052E I just ordered (which is how I came across this thread...)  :)

---

### Post by MaindotC on 2010-01-05
Since VirtualBox has had USB support, I just run the software in a Windoze VM and do it that way.  It doesn't really SOLVE the problem from an open-source perspective, but I'm not a dev and I really don't have the time to learn anything further than that :(

---

