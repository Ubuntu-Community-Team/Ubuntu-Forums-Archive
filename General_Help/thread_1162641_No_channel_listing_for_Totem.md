---
title: "No channel listing for Totem"
date: 2009-05-17
forum: General Help
---

### Post by k4kelly on 2009-05-17
Can't get the tv channels for totem. When I select watch tv a message box come up.
TOTEM is missing a channels listing to be able to tune the receiver.
Please follow the instructions provided in the link to create a channels listing.

I can find no such link. What am i missing??

---

### Post by adam_kimber on 2009-06-22
Looks like there is a bug the new version of Totem in Jaunty as the link should point to wscan. Run wscan to create a channels list. 

Use the following command line to create a channels.conf. Lots of TV programs use this so keep it safe. w_scan -ft -c GB >> /etc/vdr/channels.conf (Taken from [http://edafe.org/vdr/w_scan/](http://edafe.org/vdr/w_scan/)) If you are using a DVB-T tuner. 

Take a copy and put it here ~/.gstreamer-0.10/dvb-channels.conf

Totem should now have channel info to play back TV.

---

### Post by stmiller on 2009-09-16
Old post, but bumping with some notes.

Totem needs a 'xine' format of channels.conf

This should do it:

```
w_scan -ft -c US -X >> ~/.gstreamer-0.10/dvb-channels.conf
```

---

### Post by avacado on 2009-09-16
I am havig the same problem in jaunty.
Very confused because the command line you suggest produces an error message, it seems that the version of w_scan I am using does not accept the -c option and it is not listed under w_scan help.

w_scan [options...] 
    -a N    use device /dev/dvb/adapterN/ [default: auto detect]
    -f type    frontend type
        What programs do you want to search for?
        a = atsc (vsb/qam)
        c = cable
        t = terrestrian [default]
    -A N    specify ATSC type
        1 = Terrestrial [default]
        2 = Cable
        3 = both, Terrestrial and Cable
    -P     do not use ATSC PSIP tables for scanning
           (but only PAT and PMT) (applies for ATSC only)
    -i N    spectral inversion setting for cable TV
        DVB-T: always off
        DVB-C (0: off, 1: on, 2: auto [default])
    -F    use long filter timeout
    -t N    tuning timeout
        1 = fastest [default]
        2 = medium
        3 = slowest
    -k    generate channels.dvb for kaffeine
    -o N    VDR version / channels.conf format
        2 = VDR-1.2.x (depriciated)
        3 = VDR-1.3.x (depriciated)
        4 = VDR-1.4.x/VDR-1.5.x (default)
    -R N    radio channels
        0 = don't search radio channels
        1 = search radio channels [default]
    -T N    TV channels
        0 = don't search TV channels
        1 = search radio TV [default]
    -O N    Other Services
        0 = don't search other services [default]
        1 = search other services
    -E N    Conditional Access (encrypted channels)
        N=0 gets only Free TV channels
        N=1 search also encrypted channels [default]
    -X    tzap/czap/xine output instead of vdr channels.conf
    -x    generate initial tuning data for (dvb-)scan
    -v     verbose (repeat for more)
    -q     quiet   (repeat for less)

---

