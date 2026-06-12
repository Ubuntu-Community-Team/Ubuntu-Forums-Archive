---
title: "Desktop Optimization 1.0 (Beta)"
date: 2006-05-29
forum: Desktop Environments
---

### Post by joelbryan on 2006-05-29
Hi all,

I made a simple scripts to optimize the XML files that Ubuntu applications use.

XML Optimization is a set of method that reformat the XML metadata for use with XML stream. The process is used in websites to minimize network bandwidth consumption and increase the memory space for the applications who store them locally. XML metadata is used by modern applications like OpenOffice.org, GNOME, Evolution, Rhythmbox, GDM, etc., and is used in SVG graphic rendering. By Optimizing the XML metadata that those applications use, the application who parse them will require less memory usage, and less time parsing, thus improving speed and responsiveness.

Downloads of the scripts are available here: [http://www.gnomefiles.org/app.php?soft_id=1397](http://www.gnomefiles.org/app.php?soft_id=1397)

All of them require root permission, except rhythmbox-quickstart

NOTE: Before running the script, I ask to clock the plain version and the optimized version. tools like sysprof, valgrind, and time, or /usr/bin/time, (not the same). can help. Please post your results here.

The best way to see some changes is,
1. run the unoptimized app
2. run the scripts (require sudo)
3. reboot your system
4. run the optimized app.

That is because disk caching and the data stored in RAM is still resident so everything will be faster the second time.

---

### Post by rcarring on 2006-05-29
I am running openoffice-optimizer right now. How long should the process take?

---

### Post by tymanthius on 2006-05-29
Have you run tests to see what kind of improvements it makes in real world?

---

### Post by joelbryan on 2006-05-29
[QUOTE=rcarring]I am running openoffice-optimizer right now. How long should the process take?[/QUOTE]

Around 5-10 minutes, It's going to take long.

---

### Post by Belathor on 2006-05-29
He would like the community to help on benchmarks. It says that on his wiki.

EDIT:
[https://wiki.ubuntu.com/Optimization]("https://wiki.ubuntu.com/Optimization")

---

### Post by joelbryan on 2006-05-29
[QUOTE=tymanthius]Have you run tests to see what kind of improvements it makes in real world?[/QUOTE]

I see the improvements in rhythmbox to starts much faster, rhythmbox-quickstart must be run at start-up since rb reformat the xml file, but once it is executed, rb will run faster the second time.

Other improvements in responsiveness in GNOME, SVG Rendering, Metacity theme change, Evolution views change, OpenOffice.org's responsiveness.

However, I need some concrete benchmarks to measure those optimizations. Anyone here would like to help me?

---

### Post by rcarring on 2006-05-29
OK, my optimization of Open Office just finished.

Time to run 9 minutes.

VMWare machine, 128mb ram, Celeron cpu 1.5GHz, 10GB vm harddisk on NTFS partitioned 7200rpm 100GB Drive (external attached via usb2 to host machine)

Dapper Drake 6.06 beta 2 patched uptodate

---

### Post by joelbryan on 2006-05-29
I guess the best way to see some changes is
Run the unoptimize application now, then run the scripts, and re-run the optimized application after reboot.

---

### Post by Lovechild on 2006-05-29
would the correct thing not be to retain the readable XML and optimize the XML parser instead?

It's not a like we can afford 9 mins of heavy computation in the background to deploy this optimization using say a cron job..

---

### Post by rcarring on 2006-05-29
Do I need to reboot? OOo has got dreadfully slow following the last two daily updates, although this could be disk fragmentation either on the host or on the VM itself. My own (probably useless) observation is that it made minimal difference in the load time of OOo. I would estimate about ten seconds.

I doubt my experience is going to be relevant as I am running Dapper on a VM.

---

### Post by joelbryan on 2006-05-29
Please share your feedbacks with the optimized applications. does it makes any difference? how fast, how responsive, those kinds of feedbacks, etc.

---

### Post by joelbryan on 2006-05-29
[QUOTE=Lovechild]would the correct thing not be to retain the readable XML and optimize the XML parser instead?

It's not a like we can afford 9 mins of heavy computation in the background to deploy this optimization using say a cron job..[/QUOTE]

I emailed the libxml developers about it, I guess optimization really needs some discussions.

you just have to run the script once, except rhythmbox-quickstart.
I don't know the case about updated packages, though.

---

### Post by drizek on 2006-05-29
[QUOTE=rcarring]Do I need to reboot? OOo has got dreadfully slow following the last two daily updates, although this could be disk fragmentation either on the host or on the VM itself. My own (probably useless) observation is that it made minimal difference in the load time of OOo. I would estimate about ten seconds.

I doubt my experience is going to be relevant as I am running Dapper on a VM.[/QUOTE]

Yes, rebooting is VERY VERY important. Once you launch OOo it stays in ram and starts up much faster the next time.

---

### Post by rcarring on 2006-05-29
I rebooted. OOo took 1 minute 25 seconds to load. This is the first app I launched from the desktop.

This time is very disappointing and no reflection on your scripts. I have a Breezy install running Open Office 2.02 beta 2 install cd build and it loads within 25 seconds.

Either something has gone seriously wrong with OOo or my Dapper install has got heavily frgamented due to the number of times OOo has been updated recently.

I am very tempted to completely uninstall the current version and go back to the beta 2 version and NOT update it.

---

### Post by glotz on 2006-05-29
Just ran the doc optimizer. Seems to have helped. The OOo optimizer points to /usr/lib/openoffice whereas the actual folder on Ubuntu 5.10 default install is /usr/lib/openoffice2. Nice job! This all is like magic to me! ;)

---

### Post by joelbryan on 2006-05-29
[QUOTE=rcarring]I rebooted. OOo took 1 minute 25 seconds to load. This is the first app I launched from the desktop.

This time is very disappointing and no reflection on your scripts. I have a Breezy install running Open Office 2.02 beta 2 install cd build and it loads within 25 seconds.

Either something has gone seriously wrong with OOo or my Dapper install has got heavily frgamented due to the number of times OOo has been updated recently.

I am very tempted to completely uninstall the current version and go back to the beta 2 version and NOT update it.[/QUOTE]

I said previously in the Ubuntu mailing-list (around early May), that there' isn't any difference in the OOo loading time, but you'll feel the responsiveness when your inside OOo.

---

### Post by jimmygoon on 2006-05-29
[QUOTE=rcarring]I rebooted. OOo took 1 minute 25 seconds to load. This is the first app I launched from the desktop.

This time is very disappointing and no reflection on your scripts. I have a Breezy install running Open Office 2.02 beta 2 install cd build and it loads within 25 seconds.

Either something has gone seriously wrong with OOo or my Dapper install has got heavily frgamented due to the number of times OOo has been updated recently.

I am very tempted to completely uninstall the current version and go back to the beta 2 version and NOT update it.[/QUOTE]

make sure you go into the OOo options and turn off its support for JAVA VM's because that takes hours off the load time.

---

### Post by psylence on 2006-05-29
[QUOTE=rcarring]I rebooted. OOo took 1 minute 25 seconds to load. This is the first app I launched from the desktop.[/QUOTE]

Something is seriously screwed with your installation... It takes 10 seconds to run Writer here...

Running in a VM is also a pretty bad indication of true performance, though I'm sure you've taken that into account as well...

---

### Post by joelbryan on 2006-05-29
[QUOTE=psylence]Something is seriously screwed with your installation... It takes 10 seconds to run Writer here...

Running in a VM is also a pretty bad indication of true performance, though I'm sure you've taken that into account as well...[/QUOTE]

I agree

---

### Post by Lovechild on 2006-05-30
I'm getting more and more convinced the more I think about it that this while a good effort is really misguided.

a) It's a tradeoff between readability and parsing speed
b) The more we optimize the parser the less impact this hack has
c) The initial computation effort with this hack will probably be larger than the decrease in computation effort over the lifetime of a program without it. (thus the net benefit is... negative).

If the biggest increase we can get performancewise is this kind of work we should be doing really well as it is.

I think there are much bigger performance issues to look at than this. Fundamentally this is a case of optimization without data collection, we don't know what makes libxml slow because we don't have data to tell us if it is doing misguided idiotic stuff (which the general laws of software tells us that it does).

But thank you for trying.

---

### Post by GoA on 2006-05-30
I don't see any difference. However, I didn't take times for anything. And the doc-optimization didn't work. It complained about flash directory.

---

### Post by Triton on 2006-05-30
the openoffice script has worked very nice on my pc.  when from roughly 20secs to about 8 secs.

---

### Post by hype on 2006-05-30
Hi, i was just wondering if it was possible to "backup" modifications before running the script.
 I'd like to try [gnome-optimize](https://wiki.ubuntu.com/Optimization?action=AttachFile&do=get&target=gnome-optimize), but i'd like to be sure it doesnt break my Gnome ^^

---

### Post by rcarring on 2006-05-30
I don't have java installed. Usually I put in JRE 1.4, but Sun Java 1.5 is available. I do know that running Java does make a big performance hit. 

Aside from that, is the Sun Java distro available in the repos?

---

### Post by merlyn on 2006-05-30
[quote=rcarring]I don't have java installed. Usually I put in JRE 1.4, but Sun Java 1.5 is available. I do know that running Java does make a big performance hit. 

Aside from that, is the Sun Java distro available in the repos?[/quote]

Sun Java is now in multiverse.

Cheers.

---

### Post by joelbryan on 2006-05-30
[QUOTE=hype]Hi, i was just wondering if it was possible to "backup" modifications before running the script.
 I'd like to try [gnome-optimize](https://wiki.ubuntu.com/Optimization?action=AttachFile&do=get&target=gnome-optimize), but i'd like to be sure it doesnt break my Gnome ^^[/QUOTE]

Yes, just edit the script and backup the directories listed in the script.

---

### Post by Lowcountryrev on 2006-05-30
I ran all the scripts and my system feels a bit faster. I've had no problems with any of the apps that they tweaked.

Pentium Celeron 2.0
1 gig RAM
Dapper 6.06 LTS

---

### Post by hype on 2006-05-30
[QUOTE=joelbryan]Yes, just edit the script and backup the directories listed in the script.[/QUOTE]
Cheers man, will try that out. :)

Did you test the gnome script and see any improvement?
 Btw what kind of improvement i am supposed to see with this gnome-optimize script? (boot time quicker? Apps loading faster?)

---

### Post by Lowcountryrev on 2006-05-30
[QUOTE=hype]Cheers man, will try that out. :)

Did you test the gnome script and see any improvement?
 Btw what kind of improvement i am supposed to see with this gnome-optimize script? (boot time quicker? Apps loading faster?)[/QUOTE]

The apps seem to open faster, especially Open Office.  I haven't actually timed them but they "feel" faster.

---

### Post by yopnono on 2006-05-30
I did some change of a script to include the whole system is that bad?

---

### Post by patrickfromspain on 2006-05-30
[QUOTE=rcarring]I rebooted. OOo took 1 minute 25 seconds to load. This is the first app I launched from the desktop.

This time is very disappointing and no reflection on your scripts. I have a Breezy install running Open Office 2.02 beta 2 install cd build and it loads within 25 seconds.

Either something has gone seriously wrong with OOo or my Dapper install has got heavily frgamented due to the number of times OOo has been updated recently.

I am very tempted to completely uninstall the current version and go back to the beta 2 version and NOT update it.[/QUOTE]
well, you're running Ubuntu in virtual machine under win xp.. I suppose you're the best to complain about speed and responsiveness ;)

---

### Post by hype on 2006-05-30
Im not to used to scripts.
I started gnome-optimize (i renamed the file to gnome-optimized.sh) and "executed it in terminal".
Actually, my cpu seemed to be used at 99%, but no info or anythin appeared on screen, is it "normal"?
when the cpu stops calculating, i can consider it done? :p

---

### Post by hype on 2006-05-30
Ok, i've just run doc gocnf and Gnome optimize.

At the end of doc-optimize i get this output: 

"cat: /usr/share/doc/flashplugin-nonfree/Macromedia: Aucun fichier ou répertoire de ce type (no such file or directory)
/home/hype/Desktop/optimization/doc-optimize: line 39: /tmp-_tmp: Permission non accordée ("permission" not allowed)"

 For the second line, may i run the script as root (sudo) ?
I'll try to give some feedback on how this improved my system; just ran the scriptes, cant say right now.

---

### Post by glotz on 2006-05-30
joelbryan, you might want to edit the first message in this thread to suggest that people clock their apps before and after applying these scripts and publish their results.

---

### Post by ssam on 2006-05-30
[QUOTE=glotz]joelbryan, you might want to edit the first message in this thread to suggest that people clock their apps before and after applying these scripts and publish their results.[/QUOTE]

and reboot between test, because disk caching makes a huge difference to start times of applications (try rebooting, opening openoffice, closing it and opening it again and you'll see)

---

### Post by joelbryan on 2006-05-30
[QUOTE=yopnono]I did some change of a script to include the whole system is that bad?[/QUOTE]

I cannot tell if it's OK, since I take them one at a time to see if it doesn't break anything. Thousands of XML files had been optimized, and so far, nothing broke.

I guess, you can try, but it will take ages for the script to finish.

---

### Post by yopnono on 2006-05-30
[QUOTE=joelbryan]I cannot tell if it's OK, since I take them one at a time to see if it doesn't break anything. Thousands of XML files had been optimized, and so far, nothing broke.

I guess, you can try, but it will take ages for the script to finish.[/QUOTE]

Nope everything works fine after i run it.

---

### Post by Skye on 2006-05-30
I tried to do some semi-scientific benchmarks, so here goes:

Testbed: Presario Laptop with AMD Mobile Sempron 2800+ (1.6 GHz)
Running programs: stopwatch, gedit, and gnome-terminal

I attempted to use a physical stopwatch, but the batteries were dead. So, I instead used a program in apt called, surprisingly enough, stopwatch.  I couldn't switch between the two quickly enough to measure the startup time of some applications, but some measurements are timed. Here are my observations after running some of these scripts:

**Gconf:**
Before: Gconf took under a second to load (too fast to measure) with a lag that was only just noticable.  Once the application was running, it responded instantaneously.
During: The script took 32 seconds to run. (measured)
After: I think gconf started slightly faster, but once in the program, there was no noticable difference.

**Documentation:**
Before: Yelp took 3.74 seconds to load fully. (measured) Once running, the application was quick to respond, with little to no noticable lag. The man page for apt-get (man apt-get) took 4 seconds to load. (measured)
During: The script took 5 minutes 36 seconds to run. (measured)
After: Yelp took 2.54 seconds to load fully, (measured) and was just as repsonsive before as after. 'man apt-get' loaded almost instantly. (too fast to measure)

**Gnome:**
You can't really measure this one, aside from general observations.
Before: My system seemed to be perfectly responsive.
During: The script took 4 minutes 39 seconds to run. (measured)
After: No noticable effect, as far as I can tell.

**Open Office:**
Before: It took 12 seconds to load (I simply ran 'openoffice', not writer or impress or anything.)  Inside the program, menus are a little slow the first time, but speed up after that.
During: The script took 2 minutes 43 seconds to run. (measured)
After: It now takes 10 seconds to load.  There are no other noticable changes inside the program.

The biggest difference was definitely in the man pages and yelp.  The other changes seem not to have effected anything signifigantly one way or the other.

I hope this helps!

---

### Post by ssam on 2006-05-30
[QUOTE=Skye]I tried to do some semi-scientific benchmarks, so here goes:[/QUOTE]

did you reboot before timing things? other wise they'll run faster just because they are inst disk cache. the linux kernel is good at keeping any files you read in ram, so that next time you need them it does not need to find them on the disk again.

---

### Post by Skye on 2006-05-30
Yep, I timed the applications, ran all the scripts and timed them running, and then rebooted the computer and timed the applications again.

---

### Post by jimmygoon on 2006-05-30
[QUOTE=rcarring]I don't have java installed. Usually I put in JRE 1.4, but Sun Java 1.5 is available. I do know that running Java does make a big performance hit. 

Aside from that, is the Sun Java distro available in the repos?[/QUOTE]


it still tries to use one... I don't have one installed either but the option was still enabled... it uses the gcj thing...

---

### Post by joelbryan on 2006-05-30
[QUOTE=Skye]I tried to do some semi-scientific benchmarks, so here goes:

Testbed: Presario Laptop with AMD Mobile Sempron 2800+ (1.6 GHz)
Running programs: stopwatch, gedit, and gnome-terminal

I attempted to use a physical stopwatch, but the batteries were dead. So, I instead used a program in apt called, surprisingly enough, stopwatch.  I couldn't switch between the two quickly enough to measure the startup time of some applications, but some measurements are timed. Here are my observations after running some of these scripts:

**Gconf:**
Before: Gconf took under a second to load (too fast to measure) with a lag that was only just noticable.  Once the application was running, it responded instantaneously.
During: The script took 32 seconds to run. (measured)
After: I think gconf started slightly faster, but once in the program, there was no noticable difference.

**Documentation:**
Before: Yelp took 3.74 seconds to load fully. (measured) Once running, the application was quick to respond, with little to no noticable lag. The man page for apt-get (man apt-get) took 4 seconds to load. (measured)
During: The script took 5 minutes 36 seconds to run. (measured)
After: Yelp took 2.54 seconds to load fully, (measured) and was just as repsonsive before as after. 'man apt-get' loaded almost instantly. (too fast to measure)

**Gnome:**
You can't really measure this one, aside from general observations.
Before: My system seemed to be perfectly responsive.
During: The script took 4 minutes 39 seconds to run. (measured)
After: No noticable effect, as far as I can tell.

**Open Office:**
Before: It took 12 seconds to load (I simply ran 'openoffice', not writer or impress or anything.)  Inside the program, menus are a little slow the first time, but speed up after that.
During: The script took 2 minutes 43 seconds to run. (measured)
After: It now takes 10 seconds to load.  There are no other noticable changes inside the program.

The biggest difference was definitely in the man pages and yelp.  The other changes seem not to have effected anything signifigantly one way or the other.

I hope this helps![/QUOTE]

Thank you for your measurements. For GNOME, you can use gconftool for switching themes, and use valgrind or sysprof for benchmarking the process.

valgrind and sysprof are robust tools for benchmarking applications, It will display alot of information that we can pinpoint and evaluate system resource usage, and the effects of the script.

---

### Post by DonS on 2006-05-31
[QUOTE=Skye]<snip>
**Documentation:**
Before: Yelp took 3.74 seconds to load fully. (measured) Once running, the application was quick to respond, with little to no noticable lag. The man page for apt-get (man apt-get) took 4 seconds to load. (measured)
During: The script took 5 minutes 36 seconds to run. (measured)
After: Yelp took 2.54 seconds to load fully, (measured) and was just as repsonsive before as after. 'man apt-get' loaded almost instantly. (too fast to measure)
[/QUOTE]

To point out at this point:  The change in yelp performance has NOTHING to do with the script.  I have no idea what other factors are involved, but the scripts arn't actually optimizing anything that would affect yelp load time or displaying of man pages.

The biggest factor in load time for yelp is mozilla (On my machine, mozilla initialisation takes ~2.5 seconds out of 3.3 seconds load time.  The rest is spent constructing the user interface and reading in the TOC, neither of which is optimised in the scripts AFAICT).  If you want to help optimize yelp, try getting mozilla to play nice and take less time to initialise.

Loading of man pages is done within code in yelp.  An internal XML tree is build and processes with special xslt files (that can't and shouldn't be optimised as the spacing is actually important in them).  The doc-optimization stuff will only affect loading of manuals.  Try loading gnumeric manual before and after running the optimizer (rebooting in between) and see if you still see a difference.

Personally, I agree with the comments that there are better ways of optimizing (sorry).  Your only saving a very small amount of time (in the case of yelp manual loading, applying XSLT outweights the loading of XML by something like a factor of 500 to 1).  You'd be better to profile the apps and find out where the time is being used.  The XML optimisation is trying this blind.

For the 2.14 release of Yelp, I spent some time looking at optimising loading of documents.  The loading of the XML only takes a fraction of the time of what is needed (applying stylesheets, searching for specific nodes etc.).  Instead, actual in-code optimizations resulted in much bigger wins than optimising the XML would have.

Just my 2 cents

---

### Post by joelbryan on 2006-06-01
Cool, I have my first benchmark

**Plain Rhythmbox Database**

real    1m4.246s
user    0m17.920s
sys     0m2.508s

---- PC Restarted ----

**Optimized Rhythmbox Database**

real    0m55.105s
user    0m18.616s
sys     0m2.439s

---

### Post by minisori on 2006-06-20
I really doubt that putting all the xml in just 1 line whithout spaces would help to load a xml faster, unless the libxml parser does somekind of idiotic stuff on loading the data, something wich i doubt.

About the time loading an aplication its relative too, you cant expect to get always the same times, sometimes would take less time an others more time, just the fact maybe some libraries are loaded already could make anything to load faster.

---

### Post by phorque on 2006-06-20
I noticed no improvement.

---

### Post by unrater on 2008-01-28
$ time oowriter 

real    0m10.782s
user    0m0.024s
sys     0m0.012s

$ time oowriter 

real    0m5.832s
user    0m0.012s
sys     0m0.004s

hop this help something. obviously i reboot and only after that i executed oowriter otherwise it would be one second.


**By the way, can you do this for amarok? i think it would do a great optimization too**

---

