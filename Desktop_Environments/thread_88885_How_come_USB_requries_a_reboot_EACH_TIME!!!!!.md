---
title: "How come USB requries a reboot EACH TIME!??!??!?!?!"
date: 2005-11-11
forum: Desktop Environments
---

### Post by Sunnz on 2005-11-11
During transferring files between 2 computers, I often (or like to) use a usb disk....BUT in linux it doesn't detect the usb anymore after I unmounted it.... it is VERY ANNOYING how can I uset the USB the second time WITHOUT REBOOT THE MACHINEE!!!!!?????

---

### Post by earobinson on 2005-11-11
have you tryed the mount command?

---

### Post by Sunnz on 2005-11-11
Of course, it is ok the first time and it ONLY works on the first time... the problem is when I have unpluged it and try to mount it the SECOND time, where it ALWAYS requires a reboot, which is PISSING ME OFF!!!!

---

### Post by earobinson on 2005-11-11
do you get an error when you try and mount the second time? If so can you post it. Also a dmsg | tail would be nice!

(Sorry if it sounded stupid to ask if you had mounted but you never know I was thinking that your question was about your hotpluging not working)

---

### Post by Sunnz on 2005-11-11
Well usually it GNOME will automatically mount it as I insert the stick, but it doesn't with the second time, so I do sudo mount /dev/sda1 /media/usb, but that comand never ends and it just halts there. I also try to shutdown the computer and that won't even work, the only way would be to press the RESET button, just like the good old Windows days! :(

---

### Post by Sunnz on 2005-11-11
dmesg:
turn code = 0x70000
[4295059.070000] end_request: I/O error, dev sda, sector 1630746
[4295059.071000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.071000] end_request: I/O error, dev sda, sector 1630747
[4295059.071000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.071000] end_request: I/O error, dev sda, sector 1630748
[4295059.071000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.071000] end_request: I/O error, dev sda, sector 1630749
[4295059.072000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.072000] end_request: I/O error, dev sda, sector 1630750
[4295059.072000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.072000] end_request: I/O error, dev sda, sector 1630751
[4295059.072000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.072000] end_request: I/O error, dev sda, sector 1630752
[4295059.073000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.073000] end_request: I/O error, dev sda, sector 1630753
[4295059.073000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.073000] end_request: I/O error, dev sda, sector 1630754
[4295059.073000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.073000] end_request: I/O error, dev sda, sector 1630755
[4295059.074000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.074000] end_request: I/O error, dev sda, sector 1630756
[4295059.074000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.074000] end_request: I/O error, dev sda, sector 1630757
[4295059.074000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.074000] end_request: I/O error, dev sda, sector 1630758
[4295059.075000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.075000] end_request: I/O error, dev sda, sector 1630759
[4295059.075000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.075000] end_request: I/O error, dev sda, sector 1630760
[4295059.076000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.076000] end_request: I/O error, dev sda, sector 1630761
[4295059.076000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.076000] end_request: I/O error, dev sda, sector 1630762
[4295059.076000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.076000] end_request: I/O error, dev sda, sector 1630763
[4295059.077000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.077000] end_request: I/O error, dev sda, sector 1630764
[4295059.077000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.077000] end_request: I/O error, dev sda, sector 1630765
[4295059.077000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.077000] end_request: I/O error, dev sda, sector 1630766
[4295059.078000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.078000] end_request: I/O error, dev sda, sector 1630767
[4295059.078000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.078000] end_request: I/O error, dev sda, sector 1630768
[4295059.078000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.078000] end_request: I/O error, dev sda, sector 1630769
[4295059.079000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.079000] end_request: I/O error, dev sda, sector 1630770
[4295059.079000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.079000] end_request: I/O error, dev sda, sector 1630771
[4295059.079000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.079000] end_request: I/O error, dev sda, sector 1630772
[4295059.080000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.080000] end_request: I/O error, dev sda, sector 1630773
[4295059.080000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.080000] end_request: I/O error, dev sda, sector 1630774
[4295059.081000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.081000] end_request: I/O error, dev sda, sector 1630775
[4295059.081000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.081000] end_request: I/O error, dev sda, sector 1630776
[4295059.081000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.081000] end_request: I/O error, dev sda, sector 1630777
[4295059.082000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.082000] end_request: I/O error, dev sda, sector 1630778
[4295059.082000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.082000] end_request: I/O error, dev sda, sector 1630779
[4295059.082000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.082000] end_request: I/O error, dev sda, sector 1630780
[4295059.083000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.083000] end_request: I/O error, dev sda, sector 1630781
[4295059.083000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.083000] end_request: I/O error, dev sda, sector 1630782
[4295059.083000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.083000] end_request: I/O error, dev sda, sector 1630783
[4295059.085000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.085000] end_request: I/O error, dev sda, sector 1630784
[4295059.085000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.085000] end_request: I/O error, dev sda, sector 1630785
[4295059.086000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.086000] end_request: I/O error, dev sda, sector 1630786
[4295059.086000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.086000] end_request: I/O error, dev sda, sector 1630787
[4295059.086000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.086000] end_request: I/O error, dev sda, sector 1630788
[4295059.087000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.087000] end_request: I/O error, dev sda, sector 1630789
[4295059.087000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.087000] end_request: I/O error, dev sda, sector 1630790
[4295059.087000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.087000] end_request: I/O error, dev sda, sector 1630791
[4295059.088000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.088000] end_request: I/O error, dev sda, sector 1630792
[4295059.088000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.088000] end_request: I/O error, dev sda, sector 1630793
[4295059.088000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.088000] end_request: I/O error, dev sda, sector 1630794
[4295059.101000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.101000] end_request: I/O error, dev sda, sector 1630795
[4295059.112000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.112000] end_request: I/O error, dev sda, sector 1630796
[4295059.112000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.112000] end_request: I/O error, dev sda, sector 1630797
[4295059.112000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.112000] end_request: I/O error, dev sda, sector 1630798
[4295059.113000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.113000] end_request: I/O error, dev sda, sector 1630799
[4295059.113000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.113000] end_request: I/O error, dev sda, sector 1630800
[4295059.113000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.113000] end_request: I/O error, dev sda, sector 1630801
[4295059.114000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.114000] end_request: I/O error, dev sda, sector 1630802
[4295059.114000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.114000] end_request: I/O error, dev sda, sector 1630803
[4295059.115000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.115000] end_request: I/O error, dev sda, sector 1630804
[4295059.115000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.115000] end_request: I/O error, dev sda, sector 1630805
[4295059.115000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.115000] end_request: I/O error, dev sda, sector 1630806
[4295059.116000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.116000] end_request: I/O error, dev sda, sector 1630807
[4295059.116000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.116000] end_request: I/O error, dev sda, sector 1630808
[4295059.117000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.117000] end_request: I/O error, dev sda, sector 1630809
[4295059.117000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.117000] end_request: I/O error, dev sda, sector 1630810
[4295059.117000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.117000] end_request: I/O error, dev sda, sector 1630811
[4295059.118000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.118000] end_request: I/O error, dev sda, sector 1630812
[4295059.118000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.118000] end_request: I/O error, dev sda, sector 1630813
[4295059.118000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.118000] end_request: I/O error, dev sda, sector 1630814
[4295059.119000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.119000] end_request: I/O error, dev sda, sector 1630815
[4295059.119000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.119000] end_request: I/O error, dev sda, sector 1630816
[4295059.120000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.120000] end_request: I/O error, dev sda, sector 1630817
[4295059.120000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.120000] end_request: I/O error, dev sda, sector 1630818
[4295059.120000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.120000] end_request: I/O error, dev sda, sector 1630819
[4295059.127000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.127000] end_request: I/O error, dev sda, sector 1630820
[4295059.127000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.127000] end_request: I/O error, dev sda, sector 1630821
[4295059.127000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.127000] end_request: I/O error, dev sda, sector 1630822
[4295059.128000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.128000] end_request: I/O error, dev sda, sector 1630823
[4295059.128000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.128000] end_request: I/O error, dev sda, sector 1630824
[4295059.128000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.128000] end_request: I/O error, dev sda, sector 1630825
[4295059.141000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.141000] end_request: I/O error, dev sda, sector 1630826
[4295059.144000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.144000] end_request: I/O error, dev sda, sector 1630827
[4295059.144000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.144000] end_request: I/O error, dev sda, sector 1630828
[4295059.145000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.145000] end_request: I/O error, dev sda, sector 1630829
[4295059.145000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.145000] end_request: I/O error, dev sda, sector 1630830
[4295059.145000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.145000] end_request: I/O error, dev sda, sector 1630831
[4295059.146000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.146000] end_request: I/O error, dev sda, sector 1630832
[4295059.146000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.146000] end_request: I/O error, dev sda, sector 1630833
[4295059.147000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.147000] end_request: I/O error, dev sda, sector 1630834
[4295059.147000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.147000] end_request: I/O error, dev sda, sector 1630835
[4295059.147000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.147000] end_request: I/O error, dev sda, sector 1630836
[4295059.148000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.148000] end_request: I/O error, dev sda, sector 1630837
[4295059.148000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.148000] end_request: I/O error, dev sda, sector 1630838
[4295059.148000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.148000] end_request: I/O error, dev sda, sector 1630839
[4295059.158000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.158000] end_request: I/O error, dev sda, sector 1630840
[4295059.159000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.159000] end_request: I/O error, dev sda, sector 1630841
[4295059.160000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.160000] end_request: I/O error, dev sda, sector 1630842
[4295059.160000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.160000] end_request: I/O error, dev sda, sector 1630843
[4295059.160000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.160000] end_request: I/O error, dev sda, sector 1630844
[4295059.161000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.161000] end_request: I/O error, dev sda, sector 1630845
[4295059.161000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.161000] end_request: I/O error, dev sda, sector 1630846
[4295059.161000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.161000] end_request: I/O error, dev sda, sector 1630847
[4295059.170000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.170000] end_request: I/O error, dev sda, sector 1630848
[4295059.173000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.173000] end_request: I/O error, dev sda, sector 1630849
[4295059.173000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.173000] end_request: I/O error, dev sda, sector 1630850
[4295059.183000] SCSI error : <0 0 0 0> return code = 0x70000
[4295059.183000] end_request: I/O error, dev sda, sector 1630851
[4295059.184000] usb 5-2: USB disconnect, address 2
[4295960.778000] ipw2200: Firmware error detected.  Restarting.
[4298757.245000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298757.245000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298757.305000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298757.305000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300226.491000] ipw2200: Firmware error detected.  Restarting.
[4301438.129000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4301438.129000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4301438.217000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4301438.217000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303589.087000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303589.087000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303589.122000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303589.122000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303916.259000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303916.259000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303916.340000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303916.340000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303948.721000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303948.721000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303948.818000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303948.818000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304535.593000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4304535.593000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304535.685000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4304535.685000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

---

### Post by Sunnz on 2005-11-11
So no, there is no error the second time, it just enters an endless loop of nothing.

---

### Post by Sunnz on 2005-11-12
The situration has gone worse, now it doesn't even work, UNLESS it is already plug in before I turn on the computer. It is REALLY BAD, as I need to use my usb drive ALOT.

---

### Post by Sunnz on 2005-11-12
Here's the last few lines of dmesg:

[4295068.521000] SCSI error : <0 0 0 0> return code = 0x70000
[4295068.521000] end_request: I/O error, dev sda, sector 1731987
[4295068.521000] SCSI error : <0 0 0 0> return code = 0x70000
[4295068.521000] end_request: I/O error, dev sda, sector 1731988
[4295068.521000] SCSI error : <0 0 0 0> return code = 0x70000
[4295068.521000] end_request: I/O error, dev sda, sector 1731989
[4295068.522000] SCSI error : <0 0 0 0> return code = 0x70000
[4295068.522000] end_request: I/O error, dev sda, sector 1731990
[4295068.522000] SCSI error : <0 0 0 0> return code = 0x70000
[4295068.522000] end_request: I/O error, dev sda, sector 1731991
[4295068.522000] SCSI error : <0 0 0 0> return code = 0x70000
[4295068.522000] end_request: I/O error, dev sda, sector 1731992
[4295068.523000] SCSI error : <0 0 0 0> return code = 0x70000
[4295068.523000] end_request: I/O error, dev sda, sector 1731993
[4295068.523000] SCSI error : <0 0 0 0> return code = 0x70000
[4295068.523000] end_request: I/O error, dev sda, sector 1731994
[4295068.524000] SCSI error : <0 0 0 0> return code = 0x70000
[4295068.524000] end_request: I/O error, dev sda, sector 1731995
[4295068.524000] usb 5-1: USB disconnect, address

---

### Post by NeoChaosX on 2005-11-12
Post the contents of your /etc/fstab file. I have an idea why this is happening, I jsut need to confirm it.

---

### Post by Sunnz on 2005-11-13
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               reiserfs noatime         0       1
/dev/hda2       /boot           ext2    noatime,noauto   0       2
/dev/hda6       /home           reiserfs noatime         0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0



The almost same thing happens on the live CD as well... the live CD is hoary. Have anyone had the same problem before?

---

### Post by art on 2005-11-13
when you reinsert your jump drive in what is in the /etc/mtab, also do "sudo fdisk -l" to see what is mounted...
HTH

---

### Post by Jemm on 2005-11-13
I know with me that Ubuntu 5.10 will increment the device  if I unplug and then replug my USB HD during a session.  So for instance when the machine boots with the drive plugged in it shows up as device **/dev/sda** and if I unplug and then reconnect the drive without a reboot, it shows up as **/dev/sdb**

but since you appear to be using gnome's automount and not fstab, My problem probably has nothing to do with yours.

What filesystem is on the drive?
Are you trying to share between a Windows and Ubuntu box?  
Have you tried fsck on the device to see if it shows up any errors?

Jemm

---

