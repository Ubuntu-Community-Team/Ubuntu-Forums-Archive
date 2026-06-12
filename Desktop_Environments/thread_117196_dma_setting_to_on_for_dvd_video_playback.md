---
title: "dma setting to on for dvd video playback"
date: 2006-01-14
forum: Desktop Environments
---

### Post by robkenbat on 2006-01-14
Sorted out the necessary win32 codecs for totem and xine, but the dma wont switch to on. It keeps failing with the error message access denied.  I'm using the command:    hdparm -d1 /dev/dvd    and tried:  hdparm -d1 /dev/dvd/dev/dvd setting using_dma to 1 (on) using dma  = 1

  I must be missing something as the video is not smooth playing.

Any ideas?

---

### Post by PapaWiskas on 2006-01-14
This is what I did...hope it helps

[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

To enable DMA, you need to use the hdparm command and the configuration file hdparm.conf.
These instructions assume that you are trying to enable DMA on hdc, usually the CD-rom drive.

   1.
      See the what the settings are on /dev/hdc
                         sudo hdparm /dev/hdc
   2.
      If you get a line like  using_dma    =  1 (on), DMA is already enabled. Skip to step 4 to see if it has been enabled at boot time.
   3.
      Enable DMA on /dev/hdc
                         sudo hdparm -d1 /dev/hdc
       4.
      You have now enabled DMA for the drive. However, in order for the settings to be automatically applied at boot there you need to edit the /etc/hdparm.conf} script. To do this use this command: sudo gedit /etc/hdparm.conf

Add the following to the end of your hdparm.conf

        /dev/hdc {
         dma = on
         }

---

### Post by GeneralZod on 2006-01-14
[QUOTE=robkenbat]Sorted out the necessary win32 codecs for totem and xine, but the dma wont switch to on. It keeps failing with the error message access denied.  I'm using the command:    hdparm -d1 /dev/dvd    and tried:  hdparm -d1 /dev/dvd/dev/dvd setting using_dma to 1 (on) using dma  = 1

  I must be missing something as the video is not smooth playing.

Any ideas?[/QUOTE]

```

*sudo* hdparm -d1 /dev/dvd

```?

---

