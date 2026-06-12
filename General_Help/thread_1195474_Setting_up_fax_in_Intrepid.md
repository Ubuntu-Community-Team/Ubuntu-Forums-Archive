---
title: "Setting up fax in Intrepid"
date: 2009-06-23
forum: General Help
---

### Post by JKyleOKC on 2009-06-23
I need help getting efax set up in my Intrepid box, which has a Conexant hsfmodem in it. Here's the relevant data from lshw:

```
        *-communication
             description: Communication controller
             product: HSF 56k Data/Fax/Voice/Spkp (w/Handset) Modem
             vendor: Conexant Systems, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=hsfpcibasic2 latency=32 module=hsfpcibasic2
```

and here's the log from an attempt to verify auto-answering on my phone line:

```
***** Beginning fax log: 1853 CDT 23 Jun 2009 *****

efax-0.9a: 18:53:07 opened /dev/modem
efax-0.9a: 18:53:08 using hsfmodem-7.68.00.09oem in class 1
efax-0.9a: 18:53:09 waiting for activity
efax-0.9a: 18:53:32 activity detected
efax-0.9a: 18:53:37 fax call answered
efax-0.9a: 18:53:50 Error: timed out after waiting
efax-0.9a: 18:53:55 Warning: timed out after waiting
efax-0.9a: 18:53:58 Error: timed out after command: +FTH=3
efax-0.9a: 18:54:03 Warning: timed out after command: H
efax-0.9a: 18:53:37 sent CSI - answering ID
efax-0.9a: 18:53:55 received CSI - answering ID
efax-0.9a: 18:54:10 sync: dropping DTR
efax-0.9a: 18:54:14 sync: sending escapes
efax-0.9a: 18:54:20 Error: sync: modem not responding
efax-0.9a: 18:54:20 finished - invalid modem response
efax-0.9a: 18:54:20 opened /dev/modem
efax-0.9a: 18:54:26 sync: dropping DTR
efax-0.9a: 18:54:31 sync: sending escapes
efax-0.9a: 18:54:36 Error: sync: modem not responding
efax-0.9a: 18:54:36 finished - no response from modem

***** Ending fax log: 1855 CDT 23 Jun 2009 *****
```

I had simply dialed my fax line from my voice line, and listened for the tones -- which never came. The 13-second period between answering the call, and timing out, seems awfully short and might explain why the rest of the test failed. However since that test the modem doesn't respond to any communication attempt -- and when I shutdown or reboot the system, I see several screens full of error messages from the modem driver but they go by too rapidly to make out or capture.

I installed the modem driver using the hsfmodem-7.80.02.03full-dellhybrid.tar version posted as an attachment to another forum message and when tested using minicom, the modem appears to respond normally to such commands as AT&V or the ATIn series. It does go to +FCLASS=1 properly. However attempting to dial out via ATDT commands does nothing at all.

The kicker is that this box dual boots with Win98SE, and under Win98SE the modem both sends and receives faxes using MightyFax, with no problem. If I can get it to operate properly under Xubuntu that will remove the last barrier to wiping Win98SE entirely off, but I'm out of troubleshooting ideas. Help!!!

---

### Post by synapsys on 2009-06-23
Maybe this will help.... sorry I don't have the patience to read it all...

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1015673](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1015673)

---

### Post by JKyleOKC on 2009-06-23
That may hold the answer; many thanks! On page 5 of that thread there's mention of the no-tone-generated symptom that I have although it's for a different vendor/product code. I'll see whether the change suggested there cures things for me also and will report my findings in this thread...

---

