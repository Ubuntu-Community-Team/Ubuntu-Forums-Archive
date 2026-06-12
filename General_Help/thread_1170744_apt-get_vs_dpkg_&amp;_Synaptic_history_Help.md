---
title: "apt-get vs dpkg &amp; Synaptic history Help"
date: 2009-05-26
forum: General Help
---

### Post by sekura on 2009-05-26
Hey. I recently got cofused. I've re-installed Ubuntu 9.04 several days. Now from what i remember, the History (File -> History) of Synaptics Package Manager showed me all package installation/uninstallation history, even what i installed from the terminal, before reinstalling. Now, i see only apps installed via synaptic. Is that normal?

Now another question. Is Synaptic using dpkg to manage packages (that's what my recent forum research told me)? I got used with apt-get from the terminal. Which is better? And don't the two of them interfere with one another? If i install something from Synaptics and uninstall it from terminal apt-get? 

Could someone clear up how these three elements come together and become useful? The log from apt /var/log/apt/term.log includes the logs from synaptic /root/.synaptic/log but not viceversa.

---

### Post by michy99 on 2009-05-26
It is my understanding that both Synaptic and the Add/Remove in the Applications menu use apt-get to perform their functions.

---

### Post by sekura on 2009-05-26
Hey, thanks for the repy.
I assumed it used dpkg while reading on the forum:
"Synaptic uses dpkg underneath.
So the log is really just /var/log/dpkg.log"
source: [http://ubuntuforums.org/showthread.php?t=199433&highlight=synaptic+log](http://ubuntuforums.org/showthread.php?t=199433&highlight=synaptic+log)

Well, if you're right, then here lies my problem: Why doesn't my Synaptic history window show me install packages from within the terminal apt-get? (they appear in /var/log/apt/term.log, but not in /root/.synaptic/log witch is what the history window shows).
It seems my remembering that this was actually happening before reinstalling is right... But why not now? Have i twitched some wrong buttons?:-s

---

