---
title: "Help a dude out - lirc took away my serial port"
date: 2005-07-05
forum: Desktop Environments
---

### Post by slimsam1 on 2005-07-05
I just set up and now use the IR remote that comes on the Leadtek WinTV 2000 XP Deluxe. I used to have bottlerocket ($ br) working to turn on and off my x10-connected lights, but after installing and configuring lirc, bottlerocket no longer works. Here's what br says:
```

mike@zone:~$ br -n 2
br: error: [No such file or directory] Unable to open serial port
```
        
The switch "-n 2" means "turn on the light above mike's bed."

I tried this to no avail:```

        mike@zone:~$ sudo setserial /dev/ttyS0 uart none
        mike@zone:~$ br -n 2
        br: error: [No such file or directory] Unable to open serial port
```
        
Here's how I went about installing lirc:

1) Downloaded and extracted linux-source-2.6.10, ran make oldconfig, added Rules.make
2) Downloaded and extracted lirc-0.7.1pre4.tar.bz2, ran ./setup.sh, ran make, make install
3) After not finding the /etc/init.d/lirc script which I wanted to use instead of lircd &, I ran apt-get install lirc.
4) The init script was now there so I added it to my default runlevel.
5) I modified /etc/udev/udev.rules as follows:```

        ADDED:
        ## lircd stuff 2005-07-04 by Mike
        KERNEL="lirc0", SYMLINK="lirc"
```
        6) Ran chmod 666 /dev/lirc to fix a permissions problem.
7) Rebooted, added irexec and irxevent to my default gnome session.
8) Played with my ~/.lircrc which is now working fine.

Then I tried to assign a button on my remote to toggle my light... and it didn't work so I ran the br command manually and was given the nasty error cited above.


What happened? Does my NON-serial IR remote take over the serial port? If so, is it absolutely necessary? To clarify, I only have one device attached to my physical serial port, and that is the x10 control module.

How can I get my serial port back?

Thanks

PS: Here is my lsmod, if it's useful. (I know I have loads of modules... they are loaded by Ubuntu I guess. I haven't noticed a slowdown so they're staying for now.)
```


	Module                  Size  Used by
        proc_intf               4100  0
        freq_table              4100  0
        cpufreq_userspace       4572  0
        cpufreq_ondemand        6172  0
        cpufreq_powersave       1920  0
        video                  16260  0
        sony_acpi               6280  0
        pcc_acpi               11264  0
        button                  6800  0
        battery                10244  0
        container               4608  0
        ac                      4996  0
        ipv6                  229504  13
        snd_bt87x              12612  0
        emu10k1_gp              3840  0
        snd_emu10k1            81668  4
        snd_rawmidi            22944  1 snd_emu10k1
        snd_seq_device          8332  2 snd_emu10k1,snd_rawmidi
        snd_ac97_codec         64608  1 snd_emu10k1
        snd_pcm_oss            47652  1
        snd_mixer_oss          16768  2 snd_pcm_oss
        snd_pcm                84872  5 snd_bt87x,snd_emu10k1,snd_ac97_codec,snd_pcm_osssnd_timer              23300  1 snd_pcm
        tsdev                   7488  0
        snd_page_alloc          9604  3 snd_bt87x,snd_emu10k1,snd_pcm
        snd_util_mem            4608  1 snd_emu10k1
        snd_hwdep               9220  1 snd_emu10k1
        snd                    50276  13 snd_bt87x,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
        soundcore               9824  3 snd
        usbhid                 29376  0
        shpchp                 86116  0
        pci_hotplug            30512  1 shpchp
        forcedeth              16128  0
        ehci_hcd               29444  0
        ohci_hcd               19848  0
        usbcore               107384  4 usbhid,ehci_hcd,ohci_hcd
        nvidia_agp              7452  1
        analog                 10784  0
        gameport                4608  2 emu10k1_gp,analog
        floppy                 54864  0
        pcspkr                  3816  0
        rtc                    12216  0
        nls_iso8859_1           4224  1
        nls_cp437               5888  1
        vfat                   12928  1
        fat                    37792  1 vfat
        evdev                   9088  0
        md                     43856  0
        dm_mod                 53116  1
        capability              5000  0
        commoncap               7808  1 capability
        w83627hf               25248  0
        eeprom                  7448  0
        i2c_sensor              3584  2 w83627hf,eeprom
        i2c_isa                 2176  0
        i2c_nforce2             6400  0
        lirc_gpio               8496  1
        tuner                  20388  0
        bttv                  142928  1 lirc_gpio
        video_buf              20484  1 bttv
        firmware_class          9728  1 bttv
        i2c_algo_bit            9224  1 bttv
        v4l2_common             5888  1 bttv
        btcx_risc               4744  1 bttv
        i2c_core               21264  8 w83627hf,eeprom,i2c_sensor,i2c_isa,i2c_nforce2,tuner,bttv,i2c_algo_bit
        videodev                9728  1 bttv
        lirc_dev               12260  1 lirc_gpio
        nvidia               3923388  12
        agpgart                31784  2 nvidia_agp,nvidia
        mousedev               11160  1
        parport_pc             34372  1
        lp                     10792  0
        parport                33480  2 parport_pc,lp
        ide_cd                 38532  0
        cdrom                  36508  1 ide_cd
        psmouse                19336  0
        ext3                  120968  5
        jbd                    54168  1 ext3
        ide_generic             1664  0
        ide_disk               18176  10
        amd74xx                13340  1
        ide_core              118988  4 ide_cd,ide_generic,ide_disk,amd74xx
        unix                   26164  1038
        thermal                13576  0
        processor              22708  1 thermal
        fan                     4612  0
        fbcon                  34048  71
        font                    8448  1 fbcon
        bitblit                 5120  1 fbcon
        vesafb                  6948  1
        cfbcopyarea             3968  1 vesafb
        cfbimgblt               3072  1 vesafb
        cfbfillrect             3584  1 vesafb
```

---

### Post by slimsam1 on 2005-07-05
Bump! I still need help with this  :)

---

