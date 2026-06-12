---
title: "Strange Video Issue"
date: 2006-07-04
forum: Desktop Environments
---

### Post by SuperMike on 2006-07-04
I received a new old 1Ghz PC at my office, took it home (because it was a gift after the company upgraded PCs), put Ubuntu Breezy on it, and for some reason when I click a submit button on a web page enough times in Firefox, I either get:

* A white page and X appears dead with no keystrokes responding, no beeps, nothing. CTRL+ALT+BACKSPACE does nothing, as does CTRL+ALT+F1 or CTRL+ALT+DEL.

* Same thing, but whatever page I was on, a smidgen of pixels across the screen are "grabbed" and smeared up and down, giving a vertical set of colored streaks that sort of match the colors used on the web page I was visiting.

I tried to use another username profile and I get the same result.

I tried to completely uninstall firefox with 'apt-get --purge remove firefox' as well as 'rm -rfd /usr/lib/mozilla-firefox' and 'rm -rfd ~/.mozilla'. Then, I reinstalled firefox along with everything else it needed including Ubuntu Desktop, etc.

I rebooted and received the same result. I am forced to reboot when this problem occurs.

Other Ubuntu Breezy 5.10 systems on my home LAN do not exhibit this problem when visiting the same web pages and recreating the steps.

I'm beginning to think something's wrong in my xorg.conf file, or I have an IRQ or PCI bridge issue, or the videocard is bad. What information would you like to see or steps do you think I should take to give me your assessment?

Note this Dell system has an onboard videocard and a Trident 4MB videocard. When the system boots up, it recognizes this Trident videocard.

I noticed that no other applications on the system exhibit this problem -- only Firefox.

---

### Post by SuperMike on 2006-07-05
So far so good. I uninstalled xserver-xorg completely, then switched to universe mode and reinstalled xserver-xorg:

apt-get install xserver-xorg*
apt-get install ubuntu-desktop

All seems well now.

----

MORE DETAIL:

- Trident 3DImage 9750 (sometimes referred to as Trident 9750 or Trident 975)
- AGP slot
- Had to turn on Dell BIOS "Enable VideoDAC Snooping" or, if I did not, then I would get a bug where the mouse would leave video residue on the screen sort of like multicolored snow.
- 4MB (4096K) RAM on board
- will permit me at least 16 bit color and 1024x768. I don't dare mess with it and go to 24 bit color or increase resolution, but I can't see the diff. between 16 bit and 24 bit color with my own eyes, anyway. Besides, 16 bit runs faster. I'm find with it at this color depth and resolution.
- Heard about having to set ClockChipset to "tgui" in xorg.conf, but I guess I don't have to go to that extreme. Works fine now so far.
- Doesn't appear to permit 3ddesktop to work with direct rendering.

---

### Post by beercz on 2006-08-06
Thanks for this SuperMike, I had a strange video problem with all my media players installed on Dapper, see [http://ubuntuforums.org/showthread.php?p=1346276]("http://ubuntuforums.org/showthread.php?p=1346276").

Reinstalling xserver-xorg from the universe reporsitories seemed to have fixe d my problem.

Thanks again.

---

