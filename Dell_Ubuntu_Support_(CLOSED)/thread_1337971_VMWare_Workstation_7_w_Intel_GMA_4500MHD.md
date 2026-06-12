---
title: "VMWare Workstation 7 w/ Intel GMA 4500MHD"
date: 2009-11-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by charish2k1 on 2009-11-25
I'm running Karmic Koala at the moment (kernel's the initial one from installation) on a Dell Latitude E4200 (click [here]("http://www.dell.com/us/en/enterprise/notebooks/laptop_latitude_e4200/pd.aspx?refid=laptop_latitude_e4200&cs=555&s=biz") for specs). I have a VM currently running WinXP Pro SP3 and I've been trying for the past week now to try and get 3D acceleration working because every time I start up the VM, VMWare barks at me with the following warning:

"This computer does not have a graphics system supported by VMWare Workstation."

I've been Googling around and haven't found anything that's worked. The two solutions I've tried thus far:

1) Editing the .vmx file for the VM in question with the option to "Accelerate 3D graphics" checked in the VM's actual settings. I also went through VMWare's settings and disabled all cursor options like many guides have suggested. I've read The lines I added to the .vmx:

```
vmmouse.present = "FALSE"
mks.enable3d = "TRUE"
svga.vramSize = "67108864"
```

2) WineD3D on the guest OS as according to the instructions (installing while in Safe Mode, etc.)

[IMG]http://img.photobucket.com/albums/v60/charish2k1/Screenshot-2.png[/IMG]

Neither of these have produced any joy as the above screenshot shows =( In both cases, running "dxdiag" and the on the host machine showed that Direct3D isn't even enabled or installed. 

I would like to try and get this working so I can do some light gaming. Otherwise, I find myself (dare I say) switching to Windows 7 for my laptop which I'd like to avoid since I already have it on my desktop and I like to experience both OS's for what they're capable of.

---

