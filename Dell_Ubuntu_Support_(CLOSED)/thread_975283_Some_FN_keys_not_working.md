---
title: "Some FN keys not working"
date: 2008-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by neur0 on 2008-11-08
I got a weird problem after upgrading to 8.10:
Some fn keys on my Vostro 1310n stopped working.
Keys that stopped working: Sleep (fn + f1), Numeric keypad keys (only numbers, *-+ and / work fine) although when I go num_lock - numbers work, and I believe battery (fn + f3). Other fn keys work (brightness, volume, mute, prnt scrn...).
I tried changing the keyboard layout to evdev-managed, and I know the keys are recognized by Ubuntu as I can set the sleep button (XF86Standby) to "suspend" in System > Preferences > Keyboard Shortcuts, but it doesn't do anything.
I also tried setting the keyboard layout to Dell or some other Dell laptop (there is no Vostro), but nothing changed.

EDIT: Just to clarify, they worked fine before the upgrade.

---

### Post by Mechaphoenix25 on 2008-11-11
Same exact problem, 8.10 clean install, Dell Inspiron 1501.  Judging by the number of different threads with very similar issues, I think there's something up with Intrepid and Dell laptop keyboards.  I also tried changing keyboard layouts to no effect, and have the exact same sets of working/non-working fn+keys.  Any ideas on a fix? or a place I can report the bug?

---

### Post by Cobra78 on 2008-11-12
Same problem with a Dell inspiron 1720.

Loose fn + f1 (hibernate), fn + f3 (battery information) and fn + f5 (bloc scorr)

fn + f8 (lcd/crt switch) fn + f11 and fn + f12 are working fine :|

---

### Post by giorgiop5 on 2008-11-13
Also got similar problems with the Ubuntu 8.10 Intrepid Ibex upgrade and a Dell D410 laptop:

fn esc: Standby works
fn f1: Hibernate doesn't work
fn f2: Wireless works
fn f3: Battery doesn't work
fn f4: Num works
fn f5: Scroll doesn't work
fn f8: CRT/LCD doesn't work
fn f10: CD eject doesn't work
fn f11: PrntScrn works
fn f12: Pause/Break don't know
fn End: Mute works
fn ArrowUp: BrightnessUp works
fn ArrowDown: BrightnessDown works
fn PgUp: VolumeUp works
fn PgDn: VolumeDown works

The one that really bothers me is fn f8 to switch to the beamer for presentations. This worked fine with 8.02 Hardy Heron.

Any clue?

Cheers.
-- Giorgio


**** 2008-11-14: Found a fix for the crt lcd switch using xrandr
[http://ubuntuforums.org/showthread.php?t=965861&highlight=crt+lcd](http://ubuntuforums.org/showthread.php?t=965861&highlight=crt+lcd)
[http://yyhh.org/node/12](http://yyhh.org/node/12)

Still looking for a way to link that to the fn f8 key...

---

### Post by neur0 on 2008-11-15
Just an update:
I haven't been able to solve this and have reverted back to Hardy and everything works as intended again.

---

### Post by superm1 on 2008-11-15
update to intrepid-proposed per this bug:

[https://bugs.edge.launchpad.net/ubuntu/+bug/261721](https://bugs.edge.launchpad.net/ubuntu/+bug/261721)

You'll need the linux-image-2.6.27-8 and linux-restricted-modules-2.6.27-8 and linux-headers-2.6.27-9

---

### Post by 081105jk on 2008-11-16
&#20013;&#22269;&#183;&#30333;&#21767;&#40575;&#31199;&#36161;&#26377;&#38480;&#20844;&#21496; &#19994;&#21153;&#28085;&#30422;&#20102;&#24314;&#35774;&#24179;&#38754;&#21450;&#31435;&#20307;&#20572;&#36710;&#24211;&#20174;&#36164;&#37329;&#12289;&#35774;&#35745;&#12289;&#29983;&#20135;&#12289;&#23433;&#35013;&#12289;[**&#31435;&#20307;&#36710;&#24211;**](http://www.bjbcl.com/neiye.htm)&#21806;&#21518;&#26381;&#21153;&#12289;[**&#31435;&#20307;&#36710;&#24211;**](http://www.bjbcl.com/neiye.htm)&#32463;&#33829;&#31649;&#29702;&#31561;&#20840;&#36807;&#31243;&#30340;&#26381;&#21153;&#65292;[**&#20572;&#36710;&#35774;&#22791;**](http://www.bjbcl.com)&#20174;&#32780;&#24418;&#25104;&#20197;&#35774;&#35745;&#29983;&#20135;&#19982;&#32463;&#33829;&#31649;&#29702;&#30456;&#32467;&#21512;&#65292;&#20197;&#38596;&#21402;&#30340;&#36164;&#37329;&#23454;&#21147;&#19982;&#22810;&#26679;&#30340;&#25237;&#34701;&#36164;&#25163;&#27573;&#30456;&#32467;&#21512;&#30340;&#36816;&#20316;&#27169;&#24335;&#65292;[**&#31435;&#20307;&#36710;&#24211;**](http://www.bjbcl.com/neiye.htm)&#32467;&#21512;&#29992;&#25143;&#30340;&#38656;&#27714;&#65292;[**&#31435;&#20307;&#36710;&#24211;**](http://www.bjbcl.com/neiye.htm)&#21033;&#29992;&#24191;&#38420;&#30340;&#20572;&#36710;&#24066;&#22330;&#26469;&#28385;&#36275;&#26085;&#30410;&#22686;&#38271;&#30340;&#20572;&#36710;&#38656;&#35201;

---

### Post by Mechaphoenix25 on 2008-12-04
Well... not to burst anyone's bubble, but I got the new kernel updates, all my modules, including restricted, are on 2.6.27-9-generic and I still have some non-working keys.  Eject now works, and the crt/lcd button now does something... not sure what.  Stand-by, hibernate, battery, and scroll lock still do not work.  @superm1, will these be fixed in future kernel updates?  If so, I can wait, but it might be I'm doing something wrong.  The keys show up perfectly in the keboard shortcuts window just like before, but aren't responded to even afterwards by the OS.

Thanks, at least it's partially fixed now

---

### Post by superm1 on 2008-12-04
you need to be on the -10 kernel now from proposed.  The -9 just has security fixes.  -10 should eventually be published to -updates too.

---

