---
title: "kvm jaunty and windows 7"
date: 2009-05-06
forum: General Help
---

### Post by biasquez on 2009-05-06
hi, i tried to install windows 7 with virtualbox and all works fine. Then, i tried to install windows 7 with kvm/virt-manager but  when installer of windows started, i see "windows is loading files" and this hangs installer ( there is a loop of this message ). moreover i have video artifacts.

---

### Post by ikonia on 2009-05-06
I've had similar problems with older kvm releases and windows installs, it turned out to be specific options where needed to boot the windows VM to make is happy to run in kvm.

I'll see if I can dig out my notes.

---

### Post by biasquez on 2009-05-06
> **ikonia said:**
> I've had similar problems with older kvm releases and windows installs, it turned out to be specific options where needed to boot the windows VM to make is happy to run in kvm.

I'll see if I can dig out my notes.

sorry, i didn't understand howto to solve this problem...do you upgrade kvm release? (i'm using kvm 84 - default jaunty). what are "specific options"?

---

### Post by danwood76 on 2009-05-06
I managed to install windows 7 fine using kvm.
I used virt-manager to set it up, have you tried using that?

---

### Post by biasquez on 2009-05-06
> **danwood76 said:**
> I managed to install windows 7 fine using kvm.
I used virt-manager to set it up, have you tried using that?

i'm using virt-manager

---

### Post by danwood76 on 2009-05-06
When you create the virtual machine (in the wizard) make sure you select windows vista as the OS type.
I just tried with XP type and it failed to load the installer but with vista set it loaded fine.

---

### Post by biasquez on 2009-05-06
> **danwood76 said:**
> When you create the virtual machine (in the wizard) make sure you select windows vista as the OS type.
I just tried with XP type and it failed to load the installer but with vista set it loaded fine.

i selected vista as os type but it doesn't fix problem

---

### Post by danwood76 on 2009-05-06
Well maybe your ISO image is corrupt.
Did you get the image off MSDN?

If so re-download it.

The alternative is that maybe your processor doesnt support kvm?
Can you select kvm as the hypervisor?

---

### Post by biasquez on 2009-05-06
> **danwood76 said:**
> Well maybe your ISO image is corrupt.
Did you get the image off MSDN?

If so re-download it.

The alternative is that maybe your processor doesnt support kvm?
Can you select kvm as the hypervisor?

iso works fine with virtualbox, processor support kvm and i selected kvm as the hypervisor

---

