---
title: "More than one kernel?"
date: 2009-06-06
forum: General Help
---

### Post by BPWCOT on 2009-06-06
Hi there,
after installing Ubuntu, I was following the ubuntu guide book and something I don't remember made me have like 2 Ubuntu's? then I was installing linux-backports-modules-jaunty yesterday and I got one more linux genric in the boot menu.. Could anyone explain this to me please?
P.S Maybe You don't need to talk in a very complicated way.

---

### Post by Soul-Sing on 2009-06-06
> **BPWCOT said:**
> Hi there,
after installing Ubuntu, I was following the ubuntu guide book and something I don't remember made me have like 2 Ubuntu's? then I was installing linux-backports-modules-jaunty yesterday and I got one more linux genric in the boot menu.. Could anyone explain this to me please?
P.S Maybe You don't need to talk in a very complicated way.

hi,

via (the) ubuntu backports/proposed (which is by default not active) you got a new kernel. So now you have two kernels installed, which is no problem at all. I like to have two kernels installed on my system. When there are problems with your new kernel, you can choose to boot the "older" kernel.

---

### Post by BPWCOT on 2009-06-06
Actually I have 3 right now. So anyway in the new kernel do I have to configure programs again like, compiz is not working... 
I'm running dual-booting, If I was using windows vista then I restart to use Ubuntu, after like 5 seconds of ubuntu loaded I got system freeze up, any information about that?

Thank you

---

### Post by colau on 2009-06-06
> **BPWCOT said:**
> Actually I have 3 right now. So anyway in the new kernel do I have to configure programs again like, compiz is not working... 
I'm running dual-booting, If I was using windows vista then I restart to use Ubuntu, after like 5 seconds of ubuntu loaded I got system freeze up, any information about that?

Thank you
Did you do this?
```

sudo apt-get install compizconfig-settings-manager

```

---

### Post by Soul-Sing on 2009-06-06
> **BPWCOT said:**
> Actually I have 3 right now. So anyway in the new kernel do I have to configure programs again like, compiz is not working... 
I'm running dual-booting, If I was using windows vista then I restart to use Ubuntu, after like 5 seconds of ubuntu loaded I got system freeze up, any information about that?

Thank you

If you got the new kernel via ubuntu backports/prosposed, the kernel could be a little buggy. Please boot in a previous kernel, which runs fine.

---

### Post by Soul-Sing on 2009-06-06
If you are new with ubuntu I recommend not to use the ubuntu backports sources.

---

### Post by BPWCOT on 2009-06-06
> **leoquant said:**
> If you are new with ubuntu I recommend not to use the ubuntu backports sources.
The thing is that I wanted to use ipwraw instead of iwl3945 and when I type
sudo modprobe -r iwl3945 
The system totally freezes and it actually works with the ubuntu backports.


I didn't use
sudo apt-get install compizconfig-settings-manager
in this kernel, but I do have the compiz settings manager in the preferences menu

---

