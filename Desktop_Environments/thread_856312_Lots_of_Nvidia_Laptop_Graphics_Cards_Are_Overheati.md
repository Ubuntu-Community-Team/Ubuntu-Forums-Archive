---
title: "Lots of Nvidia Laptop Graphics Cards Are Overheating, Dying"
date: 2008-07-11
forum: Desktop Environments
---

### Post by Sealbhach on 2008-07-11
[http://gizmodo.com/5021713/lots-of-nvidia-laptop-graphics-cards-are-overheating-dying](http://gizmodo.com/5021713/lots-of-nvidia-laptop-graphics-cards-are-overheating-dying)

[http://www.theinquirer.net/gb/inquirer/news/2008/07/09/nvidia-g84-g86-bad](http://www.theinquirer.net/gb/inquirer/news/2008/07/09/nvidia-g84-g86-bad)


According to some reports, Nvidia G84 and G86 cards are faulty and will fail in a short time.

I have a Nvidia GeForce 8400 GT. I think it may be affected.

Anyone got any more information on this or any tips to check the card's performance in Ubuntu.

Thanks.



.

---

### Post by Sealbhach on 2008-07-11
Nothing to worry about then?



.

---

### Post by NewDisciple on 2008-07-13
My GE Force 7800 Go gave up the ghost last week.  Was using in Dell E1705.  Performed well but has had heat issues from day one.  Dell replacement price is nearly $700 US.  Found a used one on ebay for $360 something, but no way.  I was using this notebook as a desktop replacement.  Not the best way to go however.  The 700 dollars will go a long way in buying parts for the desktop I'm building myself.  For mobility I think I will buy a low end laptop without all of the power options.

---

### Post by Sealbhach on 2008-07-15
> **NewDisciple said:**
> My GE Force 7800 Go gave up the ghost last week.  Was using in Dell E1705. 

How long did it last?

By the way, anyone know how I could check the heat/temperature of my card?


.

---

### Post by NewDisciple on 2008-07-17
Lasted less than three years.  I supposed that's not too bad for usage and up time.  For the temp sensor readings I use the following.  (Not my work and I can't remember who wrote it or where I got.  I would like to give the author credit so if anyone knows please post it.)  Anyway:

1. Installing the sensor libraries
First thing's first - you need to install the libraries that allow Linux to read your sensors. To do this, install the lm-sensors library, by running the command:
sudo apt-get install lm-sensors

This will install the libraries for your motherboard's sensors. For your hard-disk sensors, you'll want to install hddtemp:
sudo apt-get install hddtemp
In Ubuntu, the install will ask you several questions. First it will ask if it should run SUID root, select "yes." It will then ask you for an interval for logging the temperature to a file; since we are going to have an applet display our system temperatures for us, this isn't necessary, so most users will be fine leaving the default of '0' and pressing enter; if you wish to log this data, however, I'd recommend a value between 2 and 10 seconds. Next, it will ask if it should run as a deamon; select yes, and leave the default values for hostname and port. Finally, it will ask if you wish for it to run on startup - select "yes."

2. Running sensors-detect
Now that your sensor libraries are installed, you need to detect your sensors! Run the command:
sudo sensors-detect

Which will probe your system for sensors. Answer "YES" to all questions! Don't just hit enter, type "YES", because at the end there will be a question for which the default answer is "no", and we'll want to answer in the affirmative.

The sensors-detect program will scan yur system, and then give you a summary, stating which sensors it has found. It will then say: I will now generate the commands needed to load the required modules. After you hit ENTER to continue, it will ask, Do you want to add these lines to /etc/modules automatically? (yes/NO) This is the question we want to make sure we answer YES to.

3. Loading the modules
Since we answered YES to the previous question, our sensor modules will be loaded by default the next time we start up. But since we don't want to have to reboot, we're going to use the information we got from the sensors-detect script to load the modules ourselves, this time only. Right above the last question will appear a list of modules that you should load, in the form of:
#----cut here----
# Chip drivers
smsc47m1
#----cut here----

You may have more, or different, items listed - that's fine! What we want to do now, to load these modules, is use the modprobe command, as follows:
sudo modprobe [module name]
So, in my case, I would type: 
sudo modprobe smsc47m1
If all goes well, you should be returned to the command-line, without any output.
4. Monitoring the sensors!
Wow, that was a lot of work! Now, let's see the rewards. On the command line, you can simply run the
sensors
command; this will output the information from your motherboard's sensors.

However, we'd rather have a graphical interface for checking up on our hardware, so let's install an applet for our Gnome desktop to keep an eye on our system's temperature. Run the command:
sudo apt-get install sensors-applet
to install the applet. Now, add the applet by right-clicking on your desktop panel, selecting "Add to Panel," and you will now see a "Hardware Sensors Monitor" applet in the System & Hardware section. Click and drag this to your panel to add it.
The applet will now say that you haven't enabled any sensors; right click on the applet and open its preferences. The first screen is for general settings:



The options here are self-explanatory; for update interval, choose a value between two and ten seconds. The second screen is where you can enable your sensors to be displayed in the applet:



Here we have my hard drive, /dev/sda, enabled. Simply check off the sensors you want to enable, and they will appear in your panel!

Conclusion
Hopefully by now, you'll see icons in your panel, with thermometers and temperature readouts, keeping you apprised of the status of your system's hardware. You'll notice that when doing intensive operations, various parts of your system will increase in temperature; this is normal, and this applet will help you keep an eye on things so nothing overheats.  

This tutorial refers to screenshots which are not present, but you will be able to follow it without them.

Okay, now I know where it came from.  [http://www.techthrob.com/tech/linuxsensors.php]("http://www.techthrob.com/tech/linuxsensors.php")

---

