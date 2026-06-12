---
title: "GUI won't start after update"
date: 2014-02-04
forum: Desktop Environments
---

### Post by Just4Fun20 on 2014-02-04
Sorry, this is a beginner's question.  

I have an older machine running Ubuntu 12.04 and XBMC.  It has a Zotac GEForce 8400GS video card.  

I did routine updates this morning and now the machine boots into a command prompt (one of the updates was the NVIDIA driver). 

"sudo startx" tells me:  "NVIDIA: API mismatch: the NVIDIA kernel module has version 173.14.39, but this NVIDIA driver component has version 304.116.  Please make sure that the kernel module and all NVIDIA driver component share the same version." 

Research indicates that I need to install / re-install the NVIDIA drivers.  I don't have the specific steps but I know they're out there. 

Based on research there seem to be two paths here.  Bringing things back to the 173 level or moving forward to the 304 level. 

My question - Should I be moving things back to 173 or should I re-install the NVIDIA 304 drivers?  Any advice on how I can make an informed decision?

TIA

---

### Post by grahammechanical on 2014-02-04
Use the Nvidia driver that works. Or use the open source Nouveau driver. We can use Recovery Mode>Resume to get to a working desktop and use Additional Drivers to change video drivers. I have heard that the latest Nvidia drivers sometimes drop support for older Nvidia graphic cards. And that may be what is happening in your case.

Regards.

---

### Post by Just4Fun20 on 2014-02-04
I think it's fairly obvious that I should "use the driver that works".  I was hoping for some guidance as to a preferred path.  Something that would perhaps turn an hour or an afternoon into a half hour.  But I should know by now that this is too much to ask of the Linux community.  It's a bit sad, really.    

Thank you for your answer and I apologize for being a little cross with the answer.  Time has value and the time invested, keeping Linux running, is getting to be a bit high. It certainly suggests I shouldn't be applying updates.

---

### Post by oldfred on 2014-02-04
this shows which card uses which legacy driver.
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

Your card is not on legacy list, so you should be just using the current version. Not sure how you installed a legacy driver when the current is the correct one.

Can you boot old kernel and then uninstall legacy driver, reboot with nomodeset boot parameter and newer kernel,  and install new nVidia driver from System Settings?
You need to fully purge old driver first or you will have conflicts.

---

### Post by steeldriver on 2014-02-04
have a look here - this method has worked for several people (including me) on 12.04 --> [http://askubuntu.com/a/396159/178692](http://askubuntu.com/a/396159/178692)

---

### Post by Just4Fun20 on 2014-02-04
Thank you.  

I was using the driver that was installed originally, a couple of years ago.  The update added new NVIDIA drivers but didn't update the kernel module.  

I used this procedure [http://choorucode.com/2013/02/07/how-to-fix-nvidia-driver-failure-on-ubuntu/](http://choorucode.com/2013/02/07/how-to-fix-nvidia-driver-failure-on-ubuntu/) to fix the problem.  
     Basically:  
          sudo apt-get purge nvidia-*
          sudo dkms status - didn't list any installed kernel modules so I didn't have to run the dkms remove command.
          sudo apt-get install nvidia-current-updates nvidia-settings-updates

It's working fine now (well, other than the usual overscan issue, which XBMC fixes). 

Thanks again.

---

