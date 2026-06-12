---
title: "Canon imageRunner C2550"
date: 2009-05-08
forum: General Help
---

### Post by daveosociologist on 2009-05-08
I am having a network printer problem. Cannon imageRunner C2550. 

Ubuntu 9.04 finds printer and has correct IP configuration.  Ubuntu also finds two drivers.  

When using the recommended driver (Foomatic/pxlcolor), printer does nothing at all. 

When using the secondary driver (Foomatic/Postscript), printer gives error: "PDL IMG Invalid Data". Any ides on how to fix this issue?

If it helps, I have run the troubleshooter and kept the .txt readouts.  Let me know if anyone wants me to post them for perusal.  

Thanks

DaveO

---

### Post by jlpilon76 on 2009-06-12
I have exactly the same problem. Did you find a solution. 

Thanks,

jlpilon76

---

### Post by daveosociologist on 2009-06-12
Unfortunately I have found that there is no solution.  The closest I came to fixing the issue was by using a program called BrightQ.  BrightQ gave a slightly different error.  In this error apparmor was getting in the way.  I tried to add the BrightQ driver to the list of drivers that apparmor was not to block but it did not change the outcome.  I have since given up on figuring out how to fix this issue.

You could try making BrightQ work.... if you figure it out let me know!

DaveO

---

### Post by daveosociologist on 2009-06-19
I keep seeing updates to the CUPS... maybe we will get lucky and get a functional driver.

---

### Post by putt1ck on 2010-01-05
Support for all Canon ImageRunners (regardless of add-on options) is available using the Canon supplied, GPLed open source, driver. For some reason this is not packaged for Ubuntu despite a deb being available that "just works", as well as the source package being provided.

Latest version here:

[http://support-my.canon-asia.com/contents/MY/EN/0100093001.html](http://support-my.canon-asia.com/contents/MY/EN/0100093001.html)

We have this working on K/Ubuntu 9.10.

"Needs packaging" bug opened here:

[https://bugs.launchpad.net/ubuntu/+bug/502920](https://bugs.launchpad.net/ubuntu/+bug/502920)

---

### Post by daveosociologist on 2010-01-13
HOLY CRAP!!!! Thank you putt1ck and thank you Malaysian cannon!!!!  Things are printing from my ubuntu system to my image runner.  Jobs are slow to get all the way through but they get there for sure.

---

### Post by daveosociologist on 2010-01-19
After using for a few days I will have to note that printing is EXTREMELY slow on the imagerunner C2550 and there seem to be several bugs.  If you can play around with a .deb file, change the dependencies of libcupsys-dev to libcupsys.  If you don't do this, your updater will try to nuke the files you need to print. Of course, the deb file is missing dependencies so it won't install with a little manipulation... I had to enlist a little assistance.  

Once you get it working, don't bother trying to print big documents.  I waited 10 minutes on a 60 slide presentation and nothing was happening still.  Today I printed an 18 page article through firefox.  It took a few minutes to start and took about 45 seconds to print each double sided page after that.

I will try to get my buddy to write a little bit about how he fixed the .deb file.

---

### Post by daveosociologist on 2010-01-19
From my buddy (note that I was a little off in the above description):

basically, i just followed these steps:[http://ubuntuforums.org/showthread.php?t=110458](http://ubuntuforums.org/showthread.php?t=110458)

you just unpack the deb, edit the control file (replacing the single word libcupsys-2 with libcups2), and repack it
of course i used vi instead of nano, but whatever

Have fun!

---

### Post by brianschimmel on 2010-10-07
Hi There,

the above links to the driver seem to be dead / 404. This is also true for the links within the bug report. Is there anyone who can point me to a working download location, or can mail the driver to brian.schimmel-at-googlemail-dot-com?

It's too sad to see that there has been a GPL driver and that it simply disappeared from the web.

with best regards,
Brian

---

### Post by daveosociologist on 2010-11-22
Unfortunately the upgrade to 10.10 nuked my printing capabilities....

---

### Post by daveosociologist on 2010-11-23
Also would note that the recommended and secondary drivers still fail to work.

---

### Post by daveosociologist on 2010-11-24
New driver link from Malaysian canon:

[http://support-my.canon-asia.com/contents/MY/EN/0100270807.html](http://support-my.canon-asia.com/contents/MY/EN/0100270807.html)

After I get the file worked up properly I will attach it to the thread and call the problem solved.

---

### Post by angkor59 on 2011-03-04
> **putt1ck said:**
> Support for all Canon ImageRunners (regardless of add-on options) is available using the Canon supplied, GPLed open source, driver. For some reason this is not packaged for Ubuntu despite a deb being available that "just works", as well as the source package being provided.

Latest version here:

[http://support-my.canon-asia.com/contents/MY/EN/0100093001.html](http://support-my.canon-asia.com/contents/MY/EN/0100093001.html)

We have this working on K/Ubuntu 9.10.

"Needs packaging" bug opened here:

[https://bugs.launchpad.net/ubuntu/+bug/502920](https://bugs.launchpad.net/ubuntu/+bug/502920)

Yes it's working and I'm now available to use our IR3025.
The link location has changed though:
[http://support-my.canon-asia.com/contents/MY/EN/0100270807.html](http://support-my.canon-asia.com/contents/MY/EN/0100270807.html)

---

### Post by daveosociologist on 2011-03-17
Thanks a bunch for the new link ([http://support-my.canon-asia.com/contents/MY/EN/0100270807.html](http://support-my.canon-asia.com/contents/MY/EN/0100270807.html))!  Printing is working again over here although I am fairly confident that another update will once again smoke printing capabilities. 

For me, I had to use the 32-bit debian driver files.  When you install you have to install the cndrvcups-common FIRST and then install the cndrvcups-ufr2 deb files.  If you don't do them both and in this order printing will not work.  I DID NOT have to mess with dependencies this time to get the files to work... also why I assume the next update will nuke the files.

For future reference, here's how to change the dependencies of a .deb:
dpkg -e cndrvcups-ufr2-uk_2.20-1_i386.deb
cd DEBIAN
vim control
tar czvf ../control.tar.gz *
ar r cndrvcups-ufr2-uk_2.20-1_i386.deb

---

### Post by llynix on 2012-01-20
The updated link seems to be:
[http://support-my.canon-asia.com/contents/MY/EN/0100270810.html](http://support-my.canon-asia.com/contents/MY/EN/0100270810.html)

Using that package I installed both of the 32-bit .deb files and my C2550 worked fine.

64-bit also seemed included.

Anthony

---

