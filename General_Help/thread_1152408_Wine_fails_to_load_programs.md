---
title: "Wine fails to load programs"
date: 2009-05-07
forum: General Help
---

### Post by Stolea on 2009-05-07
For some reason Wine stopped loading programs. I have uninstalled Wine and the programs and did a reinstall all to no avail, it won't fire.
I can get into the configure wine and uninstall options, but no matter what I do I cannot get the programs to work.
Any suggestions what could be the problem?

---

### Post by chellrose on 2009-05-07
These are programs you've used successfully in the past, I'm guessing?

I'm not sure what's going on... but try purging Wine, then reinstalling.

---

### Post by Stolea on 2009-05-07
Yep, I have been using Wine and the programs for the past 12 months without any hitches under 32bit 8.04 and 8.10. I did a clean install of 64bit 9.04 and installed wine and the programs I need to run. It behaved oddly right from the start and then just stopped. You can see the program trying to start, and then shuts down.
I am wondering if there is some issue with the 64 bit version of Ubuntu and Wine. 
I had tried the 64bit version of 8.04 on this computer but had all sorts of weird things happen and settled on the 32 bit version which worked fine. It could well be the hardware on this particular machine. Its an AMD Athlon(tm) 64 Processor 3000+ on a Gigabyte GA-K8NSC-939 motherboard.

---

### Post by chellrose on 2009-05-07
Could be the 64-bit.  I'm not familiar with that.

Sorry I couldn't be more helpful.  Good luck. :)

---

### Post by Stolea on 2009-05-07
Any other suggestions out there?

---

### Post by kennyrogersjr on 2009-05-07
You should try opening a terminal as your normal user and running a program with wine from there. You know what, open another terminal window as root and do the same thing.

Can you post both results? Let's see what we get from there.

Ken

---

### Post by Stolea on 2009-05-07
Plain termiminal gets this reply:
> peter@shop:~$ wine mailwasher
wine: could not load L"C:\\windows\\system32\\mailwasher.exe": Module not found
peter@shop:~$ libgcc_s.so.1 must be installed for pthread_cancel to work
wine client error:12: write: Bad file descriptor
libgcc_s.so.1 must be installed for pthread_cancel to work
err:seh:raise_exception Unhandled exception code 80000101 flags 1 addr 0xf7f82425
wine client error:12: write: Bad file descriptor
libgcc_s.so.1 must be installed for pthread_cancel to work
err:seh:raise_exception Unhandled exception code 80000101 flags 1 addr 0xf7f82425
wine client error:12: write: Bad file descriptor
peter@shop:~$

sudo terminal gets this 
> 
peter@shop:~$ sudo wine mailwasher
wine: /home/peter/.wine is not owned by you
peter@shop:~$ 


---

### Post by Stolea on 2009-05-08
I have a feeling that it is a combination of hardware and 64bit.
I have tried uninstalling Wine and reinstalling. I even deleted the .wine folder to make sure. When I reinstall Wine by rights it should be a clean install with no memory of any previous installs. But for some reason it still shows the previous Wine and any programs installed under it in the Applications startup drop down bar. So it would appear that there is somewhere something that is left behind from the previous installation. I have searched for it but cannot locate anything.

---

### Post by ikacer on 2009-05-08
the program in the application menu is just an symlink (probably. unless it runs after you think you've uninstalled.) also you can remove a program along with all of its setting using "mark program for complete removal" in synaptic. also, do you have the package "libgcc" installed?

---

### Post by Stolea on 2009-05-08
I did a "Complete removal with configuration files" of Wine, 3 times.
Just checked, libgcc1 is installed and does not give the option for reinstall.
Wine fails to run any program, not just my Mailwasher.

---

### Post by logos34 on 2009-05-08
I'm running latest wine on x64 8.04 Heron.  No probs (at present--knock on wood).

Had a problem a year ago with certain programs, but issue resolved itself, maybe through upgrade (kernel? gnome desktop?).  

I lean toward the problem being x64 and jaunty-specific, but that's just a guess.

---

### Post by kennyrogersjr on 2009-05-08
Have you tried a live dvd version of ubuntu on the same computer? It'll take about an hour or two, depending on computer speed and internet connection, but you could try installing wine on the live version.

I'd love to rule out the whole 64-bit OS doesn't work right on my hardware by asking if other programs work correctly. Can you run Open Office, for example? Do you have more than 4 GB of ram? Did you download the right version of Ubuntu, ie. desktop vs server or kubuntu vs xubuntu? Have you used/installed a 64-bit OS before and if so, did it function correctly then? Do you meet the minimum system requirements?

Do note, as in the past, that the *.04 versions haven't been the most stable versions for Ubuntu; the *.10 are the more accepted and stable releases.

BTW, I have been running Ubuntu 64-bit since 7.04. I have upgraded it all the way up to 9.04 with only minor problems that I was able to fix.

Ken

---

### Post by Stolea on 2009-05-09
Solved the problem by going back to 32bit on this computer. I like the 64bit, its a lot smoother and the graphics load a lot faster. But as they say, beggars can't be choosers. I am sure that its some hardware/software conflict somewhere and I don't have the knowledge or patitience to try and work it out.
I'll be building a quad intel machine in the next week or so and will give 64bit a go on that.
Thanks to all that tried to help.
Cheers

---

