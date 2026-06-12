---
title: "Flip Mino HD on GNU/Linux?"
date: 2008-12-18
forum: General Help
---

### Post by vvlist on 2008-12-18
Hello, I have searched Google, these forums, the Arch forums and wiki but have found nothing. Does anyone have a Flip Mino HD? Does it work with GNU/Linux or more specifically Ubuntu and/or Arch? Any input would be greatly appreciated, thanks.

---

### Post by japhyr on 2008-12-25
I just got one, so I'll let you know shortly!

---

### Post by vvlist on 2008-12-26
Here's what "sudo lsusb -v" outputs:
```
Bus 005 Device 006: ID 167b:2007  
Device Descriptor:                
  bLength                18       
  bDescriptorType         1       
  bcdUSB               2.00       
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0                             
  bDeviceProtocol         0                             
  bMaxPacketSize0        64                             
  idVendor           0x167b                             
  idProduct          0x2007                             
  bcdDevice            0.00                             
  iManufacturer           1 Pure Digital Inc.           
  iProduct                2 Flip Video Camcorder        
  iSerial                 3 PS50001                     
  bNumConfigurations      2                             
  Configuration Descriptor:                             
    bLength                 9                           
    bDescriptorType         2                           
    wTotalLength           32                           
    bNumInterfaces          1                           
    bConfigurationValue     1                           
    iConfiguration          0                           
    bmAttributes         0x80                           
      (Bus Powered)                                     
    MaxPower              500mA                         
    Interface Descriptor:                               
      bLength                 9                         
      bDescriptorType         4                         
      bInterfaceNumber        0                         
      bAlternateSetting       0                         
      bNumEndpoints           2                         
      bInterfaceClass         8 Mass Storage            
      bInterfaceSubClass      5 SFF-8070i               
      bInterfaceProtocol     80                         
      iInterface              0                         
      Endpoint Descriptor:                              
        bLength                 7                       
        bDescriptorType         5                       
        bEndpointAddress     0x02  EP 2 OUT             
        bmAttributes            2                       
          Transfer Type            Bulk                 
          Synch Type               None                 
          Usage Type               Data                 
        wMaxPacketSize     0x0200  1x 512 bytes         
        bInterval               0                       
      Endpoint Descriptor:                              
        bLength                 7                       
        bDescriptorType         5                       
        bEndpointAddress     0x82  EP 2 IN              
        bmAttributes            2                       
          Transfer Type            Bulk                 
          Synch Type               None                 
          Usage Type               Data                 
        wMaxPacketSize     0x0200  1x 512 bytes         
        bInterval               0                       
  Configuration Descriptor:                             
    bLength                 9                           
    bDescriptorType         2                           
    wTotalLength           32                           
    bNumInterfaces          1                           
    bConfigurationValue     2                           
    iConfiguration          0                           
    bmAttributes         0x80                           
      (Bus Powered)                                     
    MaxPower              100mA                         
    Interface Descriptor:                               
      bLength                 9                         
      bDescriptorType         4                         
      bInterfaceNumber        0                         
      bAlternateSetting       0                         
      bNumEndpoints           2                         
      bInterfaceClass         8 Mass Storage            
      bInterfaceSubClass      5 SFF-8070i               
      bInterfaceProtocol     80                         
      iInterface              0                         
      Endpoint Descriptor:                              
        bLength                 7                       
        bDescriptorType         5                       
        bEndpointAddress     0x02  EP 2 OUT             
        bmAttributes            2                       
          Transfer Type            Bulk                 
          Synch Type               None                 
          Usage Type               Data                 
        wMaxPacketSize     0x0200  1x 512 bytes         
        bInterval               0                       
      Endpoint Descriptor:                              
        bLength                 7                       
        bDescriptorType         5                       
        bEndpointAddress     0x82  EP 2 IN              
        bmAttributes            2                       
          Transfer Type            Bulk                 
          Synch Type               None                 
          Usage Type               Data                 
        wMaxPacketSize     0x0200  1x 512 bytes         
        bInterval               0                       
Device Qualifier (for other device speed):              
  bLength                10                             
  bDescriptorType         6                             
  bcdUSB               2.00                             
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0                             
  bDeviceProtocol         0                             
  bMaxPacketSize0        64                             
  bNumConfigurations      2                             
Device Status:     0x0001                               
  Self Powered
```

(Obviously I received mine)
a small window pops up saying "Unable to mount FLIPVIDEO," but it mounts anyway.
The Flip MinoHD mounts as "FLIPVIDEO" in nautilus and dolphin.
If wine is installed, you can run "Setup_FlipShare.exe" from the FLIPSHARE mount. It apparently requires Windows Media Player to run the application though, because I got and error. I used wine to install Windows Media Player 9, but FlipShare still won't open.

---

### Post by thecorfiot on 2008-12-28
> **vvlist said:**
> Hello, I have searched Google, these forums, the Arch forums and wiki but have found nothing. Does anyone have a Flip Mino HD? Does it work with GNU/Linux or more specifically Ubuntu and/or Arch? Any input would be greatly appreciated, thanks.

Hi,

Santa was good to me and delivered a Flip Mino HD!

As has already been posted, the software provided is for Macs and that other OS ;-). However, once plugged into my Lenovo laptop running Hardy, it is immediately recognised and mounted. You can navigate to the stored video and run your movies in Mplayer, Totem or whatever takes your fancy.

Obviously, the onboard software isn't going to work but I haven't tried with Wine.

I guess that those more experienced in matters video will be able to advise you about editing etc. but I cannot see that you would not be able to manipulate your gems as you would with any other avi file.

Hope that helps.

Bob G.

---

### Post by japhyr on 2008-12-30
When I play the video files in totem, they are choppy.  Do they play nicely for either of you?

---

### Post by sosaudio1 on 2008-12-30
> **japhyr said:**
> When I play the video files in totem, they are choppy.  Do they play nicely for either of you?

Try using VLC or totem with Xine instead of gstreamer.

It could also be how much horsepower you have under the hood in your comp. Remember that if you recorded in true 1080i or p mode it requires a whole lot of processor and memory to run smoothly. 

But as I have said before, you may find that VLC plays it just fine... you may also find that totem using xine works just as well....but if these dont get you anywhere, check the settings. Think about increasing your video and audio buffers. Xine-ui has a lot of settings that you can adjust to get it working...or working better....instead of totem you could try that...

Check also that you don't have any conflicts with compiz. If you are running that, I would suggest stopping compiz first and then running the video and see if that fixes it...

Beyond that, I use Xv for my video output modules and ALSA for all my audio.

Beyond that, you will have to look at your processor, ram, harddrive performance and of course, video card performance and find ways to maximize all of those parameters.

Just a little to chew on

Have Fun
Rich

---

### Post by ah pook on 2009-07-16
I can't get mine to mount!  AMD 64 bit, Intrepid 64-bit, all updates current, I've tried everything, but Linux no likey. Any ideas? I just got it today as a gift, and spent the last three hours trying to mount it. Looks like a cool little toy, but not if it won't work under Ubuntu.

---

### Post by n3had on 2009-12-14
> **ah pook said:**
> I can't get mine to mount!  AMD 64 bit, Intrepid 64-bit, all updates current, I've tried everything, but Linux no likey. Any ideas? I just got it today as a gift, and spent the last three hours trying to mount it. Looks like a cool little toy, but not if it won't work under Ubuntu.

it mounts fine on Karmic 64bit

---

### Post by japhyr on 2009-12-15
Mine works well now on Jaunty, and a new laptop with better specs.

---

### Post by deusdiabolus on 2010-02-18
Ubuntu Karmic recognizes it and will allow me to access the video files (in MP4 format in a subdir), but I can't seem to find a way to play them back properly.  Everything I have tried (VLC, mPlayer, Totem) shows a frame or two while the audio continues to stream, then shows another frame or two and then it's over.  The clips playback sluggishly from YouTube, as well.  It's probably my computer's specs (2GHz P4 with onboard audio/video).  But if there are any other suggestions...

---

### Post by C.B.Leslie on 2010-05-21
Long story short, the reason the Mino HD's H264 videos don't play well are are due to the fact that the camera shoots and compresses in the 3VIX h246 Codec. If you have windows/OSX, and you don't have 3VIX installed, you will get the same issue.

They offer the 3VIX codec (no idea how up-to-date it is or if it will even help with the situation) with "instructions" on how to use it, but I have NO idea how to execute them, or if it's even a viable option to do so.
 
[http://www.3ivx.com/download/unix.html](http://www.3ivx.com/download/unix.html)

Any help with making a nice little .deb package for an in experienced Flip Mino HD owner, would be much appreciated.

---

### Post by mikkeX on 2010-06-10
Just got an Mino HD, second generation. It works fine to play the files in VLC, but I have not find an way to save the files in other formats to make them editable in a video editing program. Handbrake converts the video, but there is no sound.

---

### Post by iamgeniusrnti on 2010-10-16
I was able to install Flipshare after installing WMP10.  But I can't convince Flipshare that I rebooted my computer.  What do I need to do if wineboot doesn't work?


```
samantha@Samantha-pc:~/.wine/drive_c/Program Files/Flip Video/FlipShare$ wine FlipShare.exe
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:win:FlashWindowEx 0x32de98
fixme:quartz:FilterGraphInner_QueryInterface unknown interface {fc4801a3-2ba9-11cf-a229-00aa003d7352}
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:quartz:FilterGraphInner_QueryInterface unknown interface {fc4801a3-2ba9-11cf-a229-00aa003d7352}
fixme:msvcrt:_set_error_mode dummy implementation (old mode: 0, new mode: 2)
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1ad5c0,0x00000010,0x32f490) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1ad5c0,0x00000020,0x32f490) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x3fd7cf8,0x00000010,0x32f024) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x3fd7cf8,0x00000020,0x32f024) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x3fd7cf8,0x00000010,0x32f024) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x3fd7cf8,0x00000020,0x32f024) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x3fd7cf8,0x00000010,0x32f024) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x3fd7cf8,0x00000020,0x32f024) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x3fd7cf8,0x00000010,0x32f024) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x3fd7cf8,0x00000020,0x32f024) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION
fixme:quartz:FilterGraphInner_QueryInterface unknown interface {fc4801a3-2ba9-11cf-a229-00aa003d7352}
fixme:quartz:AVISplitter_InitializeStreams stream 0: frames found: 0, frames meant to be found: 40
fixme:quartz:AVISplitter_InitializeStreams stream 1: frames found: 29696, frames meant to be found: 29
fixme:qedit:MediaDet_get_StreamType (0x3ff2128)->(0x7bcb7bf6): not implemented!
fixme:quartz:FilterGraphInner_QueryInterface unknown interface {fc4801a3-2ba9-11cf-a229-00aa003d7352}
fixme:quartz:AVISplitter_InitializeStreams stream 0: frames found: 0, frames meant to be found: 40
fixme:quartz:AVISplitter_InitializeStreams stream 1: frames found: 29696, frames meant to be found: 29
fixme:qedit:MediaDet_get_StreamType (0x189bc8)->(0x7bcb7e21): not implemented!
fixme:quartz:FilterGraphInner_QueryInterface unknown interface {fc4801a3-2ba9-11cf-a229-00aa003d7352}
fixme:win:FlashWindowEx 0x32dd98
fixme:win:FlashWindowEx 0x32bf98
fixme:win:FlashWindowEx 0x329a98
```

---

### Post by iamgeniusrnti on 2010-10-16
OK,

I upgraded to 1.3.4 and it runs fine but it can't see the USB camcorder.  But I can mount the camcorder easily.

Here is lsusb:

Bus 001 Device 006: ID 167b:2008... not sure if I need to add something somewhere...

---

