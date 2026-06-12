---
title: "Oscilloscope Screenshot"
date: 2009-01-26
forum: General Help
---

### Post by MaindotC on 2009-01-26
I'm taking an introductory AC analysis course and the professor wants us to take a screenshot of a [Tektronix TDS 210](http://is.gd/hhWT) oscilloscope output to turn in with our labs.  In window$ we use software called Waveform Lite (which I can't seem to find a link to) and connect the oscope to our machines using a [PL-2303](http://is.gd/hhVo) adapter.  In Ubuntu the PL-2303 is detected just fine as /dev/ttyUSB0 - in fact I've used it for console connections to routers and switches - but I can't seem to find a program to display the oscope output.  I tried [xoscope](http://is.gd/hijh) which seemed to be the closest I could get from other suggestions, and it does have an option that allows me to select /dev/ttyUSB0.  However, when I run the program with that setting I'm not getting anything - no wavy lines or anything suggesting a signal input.

Does anyone know of a program that would help me accomplish this goal, or a different forum on which to post this question if this isn't appropriate for general help?  Thanks!

---

### Post by Endolith on 2009-01-26
Again, you're trying to use xoscope in [Bitscope ]("http://www.bitscope.com/product/")compatibility mode, but that won't work with a Tektronix.

What DLL does Wine want?  Can you get it from your Windows VM installs?

[http://ubuntuforums.org/forumdisplay.php?f=169](http://ubuntuforums.org/forumdisplay.php?f=169)

---

### Post by ieee488 on 2009-01-26
> **strAlan said:**
> I'm taking an introductory AC analysis course and the professor wants us to take a screenshot of a [Tektronix TDS 210](http://is.gd/hhWT) oscilloscope output to turn in with our labs.  In window$ we use software called Waveform Lite (which I can't seem to find a link to) and connect the oscope to our machines using a [PL-2303](http://is.gd/hhVo) adapter.  In Ubuntu the PL-2303 is detected just fine as /dev/ttyUSB0 - in fact I've used it for console connections to routers and switches - but I can't seem to find a program to display the oscope output.  I tried [xoscope](http://is.gd/hijh) which seemed to be the closest I could get from other suggestions, and it does have an option that allows me to select /dev/ttyUSB0.  However, when I run the program with that setting I'm not getting anything - no wavy lines or anything suggesting a signal input.

Does anyone know of a program that would help me accomplish this goal, or a different forum on which to post this question if this isn't appropriate for general help?  Thanks!

LOL. Still at this huh?

As I wrote in the other thread you posted last week, this is not a trivial task. There is a reason your professor chose Waveform Lite.

If you want to do your "own thing", get the Tektronix Programmers Manual and learn the commands, learn how to program in a language like C or BASIC, and learn how to program gtk+.

[http://www.blii.com/metratek_wfm_mgr_lite.htm](http://www.blii.com/metratek_wfm_mgr_lite.htm)

---

### Post by MaindotC on 2009-01-26
> **ieee488 said:**
> 
If you want to do your "own thing", get the Tektronix Programmers Manual and learn the commands, learn how to program in a language like C or BASIC, and learn how to program gtk+.


I agree and I am learning but I've a feeling I won't be able to do what I need before Thursday's lab.

---

### Post by Endolith on 2009-01-26
> **strAlan said:**
> I agree and I am learning but I've a feeling I won't be able to do what I need before Thursday's lab.

I have a *very strong* feeling you won't be able to write an oscilloscope application from scratch by Thursday.  :)  

The only option I see is Wine.  If that doesn't work, use a different (lab, friend) computer.  There's a reason I have a Windows/Ubuntu dual boot.

---

### Post by arvevans on 2009-01-26
On my Tektronics THS710A Oscilloscope I use the "Hard Copy" button to transfer bitmap views of the scope screen to a linux file.  The program on linux looks like this:

[INDENT]#!/usr/bin/perl
$Port="/dev/ttyS0";
$Filename="tek.bmp";
open(OUTFILE,">$Filename");
open(SCOPE,"<$Port");
system("/bin/stty 9600 -echo -parenb raw < $Port");
select SCOPE;
$|=1;
select OUTFILE;
$i = 0;
while($i < 9662) {
        if(port_has_data())
        {
                $i++;
                sysread(SCOPE, $mychar, 1);
                print OUTFILE ($mychar);
        }
#       select(undef, undef, undef, 0.05);      # 1/20 second sleep
}
close SCOPE;
close OUTFILE;

sub port_has_data {
        my($rin,$nfd);
        vec($rin,fileno(SCOPE),1) = 1;
        return $nfd = select($rin,undef,undef,0);
        }

[/INDENT]

I found this on a web site several years ago, but don't remember who originally wrote it.

Arv
_._

---

### Post by Endolith on 2009-01-26
> **arvevans said:**
> I found this on a web site several years ago, but don't remember who originally wrote it.


Google says this: [U][http://www.bobblick.com/techref/projects/ths720/ths720.html](http://www.bobblick.com/techref/projects/ths720/ths720.html)
[/U]
He says it will not work with TDS220, so probably not with TDS210, either.

If you scope manual tells how to do serial port commands like this, maybe you can write a script to download BMPs.  No need to learn C or GTK+.  Python or Perl would be sufficient.

---

### Post by mikelygee on 2009-01-26
The code posted by arvevans looks like it came from [http://www.bobblick.com/techref/projects/ths720/ths720.html]("http://www.bobblick.com/techref/projects/ths720/ths720.html"). The author states it won't with with the TDS220, but from what I remember of those scopes I don't think it would be too hard to adapt it.

I also stumbled across [http://www.febo.com/geekworks/data-capture/tds-2012.html]("http://www.febo.com/geekworks/data-capture/tds-2012.html"), though the source code link didn't work for me.

Good luck!

---

### Post by niteshifter on 2009-01-26
Hi,

Indeed, not exactly a beginner project, but for some folks the best way to learn is by being challenged. I've written software for Tek 'scopes, years ago in Visual Basic (VB5. How quaint ;) ).

Here's a [link]("http://staff.science.uva.nl/~vlaander/docu/Tektronix/programmer_manual_TDS220.pdf") to the TDS 200 Series Programmer Manual.

Glade (for doing the UI) and Python would be a good choice for simple acquisition purposes. However, unless you're a whiz at programming, it isn't going to come together in scant days. 

Borrow what you need to get the coursework done. Or try the app in WINE or a virtualized Win.

---

### Post by Endolith on 2009-01-26
> **niteshifter said:**
> Glade (for doing the UI)

No need to do any graphical programming at all if you're just trying to get the screengrab in BMP format.

---

### Post by arvevans on 2009-01-26
In the prior post I forgot to use a preformat before listing the code.  Here is a more readable listing:


[INDENT]
[HTML]#!/usr/bin/perl
$Port="/dev/ttyS0";
$Filename="tek.bmp";
open(OUTFILE,">$Filename");
open(SCOPE,"<$Port");
system("/bin/stty 9600 -echo -parenb raw < $Port");
select SCOPE;
$|=1;
select OUTFILE;
$i = 0;
while($i < 9662) {
	if(port_has_data())
	{
		$i++;
		sysread(SCOPE, $mychar, 1);
		print OUTFILE ($mychar);
	}
#	select(undef, undef, undef, 0.05); 	# 1/20 second sleep
}
close SCOPE;
close OUTFILE;

sub port_has_data {
	my($rin,$nfd);
	vec($rin,fileno(SCOPE),1) = 1;
	return $nfd = select($rin,undef,undef,0);
	}
[/HTML]
[/INDENT]

"Endolith" is correct.  If what you want is a bitmap of the screen image, this is one way to do it.  Of course my THS710A uses an RS-323 interface.  If your scope uses USB, then you would be opening a path via the USB port and device.

---

### Post by MaindotC on 2009-01-26
I tried Wine and although I downloaded and properly installed ddeml.dll and rebooted wine it still did not detect the library.  I'll keep trying.  I'll test the script you posted as well - I won't be back in the lab till tomorrow.  I have a couple vm's of XP and Vista so I'll just use them provided I figure out how to get the vm's to detect and use the usb ports.  I appreciate your replies and thanks to everyone except ieee488.

---

### Post by ieee488 on 2009-01-27
> **strAlan said:**
> I appreciate your replies and thanks to everyone except ieee488.

LOL. Typical.

---

### Post by Endolith on 2009-01-28
[ftp://ftp.febo.com/pub/n8ur_programs/](ftp://ftp.febo.com/pub/n8ur_programs/) is back up. Doesn't look tremendously complex:

[php]#!/usr/bin/python

# tds-2012.py
# version 0.1 -- 27 Jan 2004
#
# Plot display of Tektronix TDS-2012 (or other TDS-10xx or TDS-20xx DSO)
#
# Copyright 2004 by John R. Ackermann  N8UR (jra@febo.com)
# Licensed under the GPL version 2 or later; see the file COPYING
# included with this distribution.  I request, but do not require, that
# any modifications that correct bugs or errors, or increase the program's
# functionality, be sent via email to the author at the address above.
#
# Current status:
# Version 0.1 -- first version, and first ever Python program.  Note that
#   binary read requires updated linux-gpib python bindings (post version
#   3.1.99).  If you don't have that version, you can convert to use an
#   ASCII data read as commented below.  Assumes that "scope" is defined 
#   in /etc/gpib.conf.


from Gpib import *
from matplotlib.matlab import *
from string import *
from time import *
from struct import *

# how long to sleep after issuing a write
sleeptime = 0.01

# set up GPIB comms and clear device
scope = gpib.find('scope')
gpib.clear(scope)

# set SRQ operation
gpib.write(scope,'DESE 1')
gpib.write(scope,'*ESE 1')
gpib.write(scope,'*SRE 32')

# turn off response headers and set waveform output to default binary
# it seems like these need to be sent separately and not concatenated
gpib.write(scope,'head 0')

# for ASCII dump, send 'dat ASCII' instead
gpib.write(scope,'dat INIT')
sleep(sleeptime)

# get instrument settings
gpib.write(scope,'ch1:scale?')
sleep(sleeptime)
voltsdiv = float(gpib.read(scope,80))
if voltsdiv >= 1:
    volt_string = '%i V / div' % (voltsdiv)
else:
    volt_string = '%i mv / div' % (voltsdiv * 1000)

gpib.write(scope,'hor:mai:sca?')
sleep(sleeptime)
tmp = float(gpib.read(scope,80))
rawsweep = tmp
if tmp >= 1:
    sweep_val = tmp
    sweep_suf = "S"
if tmp < 1:
    sweep_val = tmp * 10e2
    sweep_suf = "mS"
    if tmp < 0.001:
        sweep_val = tmp * 10e5
        sweep_suf = "uS"
        if tmp < 0.000001:
            sweep_val = tmp * 10e8
            sweep_suf = "nS"
sweep_val = '%.f' % sweep_val
sweep_string = sweep_val + ' ' + (sweep_suf) + " / div"

# acquire
gpib.write(scope,'acquire:state on')
sleep(sleeptime)

# get the waveform preamble
gpib.write(scope,'wfmpre?')
sleep(sleeptime)
tmp = gpib.read(scope,256)
preamble = split(tmp,';')
# number of points in trace
points = int(preamble[5])
# volts per bit (-127 to +128)
voltsbit = float(preamble[12])

# get the curve
gpib.write(scope,'curv?')
sleep(sleeptime)

# binary data read and convert to list
tmp = gpib.readbin(scope,4096)

# for ASCII read, use 'gpib.read(scope,16384)' instead of the above, and 
# delete the next two lines.  You'll need to use 'split' to convert the 
# comma-delimited values returned in 'tmp' to a list of values called
# 'tmplist', and you may need to adjust the offsets used in the 'for' loop 
# to end up with the proper number of points

formatstring = '%ib' % (len(tmp))
tmplist = unpack(formatstring,tmp)

trace = []
# there's a newline at the end of the data, thus the strange slice
for x in tmplist[len(tmplist)-points-1:-1]:
    trace.append(int(x)*voltsbit)

# get some measurements, just for fun
tmp = 9.9E37
gpib.write(scope,'measu:imm:typ PK2;:measu:imm:sou CH1')
sleep(sleeptime)
gpib.write(scope,'measu:imm:val?')
sleep(sleeptime)
tmp = float(gpib.read(scope,80))
if tmp != 9.9E37:
    peak_string = 'Pk-Pk: %.3f V' % (tmp)
else: peak_string = ''

gpib.write(scope,'measu:imm:typ MEAN;:measu:imm:sou CH1')
sleep(sleeptime)
gpib.write(scope,'measu:imm:val?')
tmp = float(gpib.read(scope,80))
if tmp != 9.9E37:
    mean_string = 'Mean: %.3f V' % (tmp)
else: mean_string = ''

gpib.write(scope,'measu:imm:typ PERI;:measu:imm:sou CH1')
sleep(sleeptime)
gpib.write(scope,'measu:imm:val?')
tmp = float(gpib.read(scope,80))
if tmp >= 1:
    period_val = tmp
    period_suf = "S"
if tmp < 1:
    period_val = tmp * 10e2
    period_suf = "mS"
    if tmp < 0.001:
        sweep_val = tmp * 10e5
        sweep_suf = "uS"
        if tmp < 0.000001:
            period_val = tmp * 10e8
            period_suf = "nS"
if tmp != 9.9E37:
    period_string = 'Period: %.3f' % (period_val) + ' ' + period_suf
else: period_string = ''

gpib.write(scope,'measu:imm:typ FREQ;:measu:imm:sou CH1')
sleep(sleeptime)
gpib.write(scope,'measu:imm:val?')
tmp = float(gpib.read(scope,80))
if tmp < 1e3:
    freq_val = tmp
    freq_suf = "Hz"
if tmp < 1e6:
    freq_val = tmp / 10e2
    freq_suf = "kHz"
if tmp >= 1e6:
    freq_val = tmp / 10e5
    freq_suf = "MHz"

if tmp != 9.9E37:
    freq_string = 'Freq: %.3f' % (freq_val) + ' ' + freq_suf
else: freq_string = ''

# plot
plot(trace)
axis([0,points,-5*voltsdiv,5*voltsdiv])
xlabel(sweep_string)
ylabel(volt_string)
set(gca(), 'xticklabels', [])
if not gca().is_first_col():
    set(gca(), 'yticklabels', [])
if not gca().is_last_row():
    set(gca(), 'xticklabels', [])
grid(1)

text(0.03*points,-4.9*voltsdiv, peak_string)
text(0.03*points,-4.4*voltsdiv, mean_string)
text(0.72*points,-4.93*voltsdiv, freq_string)
text(0.72*points,-4.4*voltsdiv, period_string)

show()
[/php]

---

