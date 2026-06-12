---
title: "Optimizing 9.04"
date: 2009-05-26
forum: General Help
---

### Post by jackstoner on 2009-05-26
I built a rig for my family and installed Ubuntu because there's no need to spend the extra money on MS when Ubuntu can do what they need. 

My question is how can I best optimize 9.04 so that its as fast and snappy as possible for them? 

Specs 
Pentium Dual-Core E5200 
Galaxy 8400 GS
Gigabyte GA-G31M-ES2L
Seasonic 300 W


Thanks

---

### Post by aesis05401 on 2009-05-26
This is actually a very involved question.  Hardcore Linux users will let you know that making a Linux box as snappy as possible involves turning off the desktop envirnoment ;)

For some more useful advice, try the finding the right level of performance for a specific type of use.  If your family mostly browses the internet then your biggest optimizations will probably occur within the browser caching/assorted preferences settings.  If you are all working in office suite programs then your optimizations may come in modifications to the loading and caching of shared runtime libraries etc.

Global stuff:

1. Try out all of the desktop rendering effects and options to see how your machine responds.  You can significantly change the perception of speed by finding the right level of GUI dressing for your machine.  If you play with the settings and find that your machine can run high levels of graphical effects that is fine, but remember that these effects come with a resource price.

2. Control downloading:  Determine whether you need to implement a bandwidth shaper.  There are a number of ways to control downloading on a shared box, but the easiest is probably user space bandwidth shaping.  One program that does this is 'trickle' but there are other methods of achieving this goal, including using onboard options in the download clients (torrent or whatever) to limit bandwidth usage.  This is only an issue if someone wants to use the communal box to do heavy and prolonged downloading - ie: one of your kids is getting into Linux and wants to try all the distros at once ;) With a proper bandwidth control strategy in place everyone can leave their jobs running without significantly impacting the current user.

3. Check for optimizations for the software you are using:  This step can become very involved.  Program suites based on runtime environments can be optimized by changing settings related to the loading and caching of shared libraries etc...  

Additionally, many GUI-based programs in the Linux world can be launched in different configurations by utilizing 'flags' or options that are passed to the program at launch either through a custom launcher or through manual entry of a CLI invocation.  To find out about options of this sort look first to the 'man' pages of the programs you use.

4. Run everything at once:  Once you have a good idea about the types of uses the machine is going to see put it through a stress test by having it do everything at once.  A little research with a search a engine should lead to strategies to iron out any hiccups you encounter when putting the machine under load (remember to turn down desktop effects first to see if the machine responds better without them while under heavy load).

5. Research the services running on your machine:  This is a long term project.  Standard Ubuntu distros come with a pretty good config out of the box, but every machine has room to be customized from the default install.  The most important thing is to never disable anything you don't understand. 

6.  Learn how to read logs.  This is the most important part of running an optimized Linux box.  I used to hate the feeling when my computer would suddenly slow way down and I couldn't figure out what was going on.  Now that your family computer is running Linux you have a powerful ability to know what is going on behind the scenes through the use of programs like iptables, snort, nmap, etc.  Each of these programs can generate logs that will tell you in detail what is happening on your network and give you the ability to control that activity.  All you need to learn is some basic configuration information and how to read log files and you are off and running on the path to complete control of your family's computing environment.  Searching teh security sections of online forums such as this one will give you lots of leads on getting started with these security appilcations.  

Finally, and most of all, listen to your users!  Let your family know that they can run kde applications under gnome and vice versa.  Most of your optimizations will come as a result of researching complaints from end-users.  The fact that you are running Linux means that with a little effort you should be able get your OS perfectly configured for the current use case.

---

