---
title: "vmware workaround help"
date: 2008-05-18
forum: Desktop Environments
---

### Post by sumone on 2008-05-18
I am trying to install vmware on a Dell Dimension 9200 running Hardy and have had the same problems as some others with a failed install. I have got part way through a workaround by Rizlaw but do not understand part of the procedure. The workaround is shown below and the problem follows:

* unpack VMware-workstation-6.0.3
* go to vmware-distrib/lib/modules/source
* untar the file vmmon.tar (tar xvf vmmon.tar)
* cd vmmon-only/include
* edit the file vcpuset.h
* go to line 74
* change #include “asm/bitops.h” to #include “linux/bitops.h” (Because there are some changes made to the 2.6.24 kernel, it’s not possible to include bitops.h from asm and you will have to include it from the linux directory)
* go back to vmware-distrib/lib/modules/source
* remove the old vmmon.tar file (rm vmmon.tar)
* repack the new vmmon.tar file (tar cvf vmmon.tar vmmon-only)
* remove vmmon-only directory (rm -rf vmmon-only)


Now go to vmware-distrib directory and install vmware as you usualy do. It should work without a glitch.
Last edited by Rizlaw; 2 Weeks Ago at 08:42 PM. 


I am fine up to changing line 74 but am doing something wrong from here, I expected to save the edited file but there was no Save option. Where it says "go back to vmware-distrib/lib/modules/source" is this via another terminal window? I am a bit lost here and will appreciate a pointer in the right direction. The workaround obviously works for others so there's no good reason why I should not be able to fix this with a bit of help

thanks in advance
DJ

---

### Post by dushkal on 2008-05-20
Disabled save option has probably to do with the file permissions. Check that, most likely since VMware requires root user to run the installation the file permissions do not allow normal users to edit it. Try using sudo vi vcpuset.h when editing the file. or if you are using gui, then press alt-F2 and type gksudo gedit vcpuset.h

---

