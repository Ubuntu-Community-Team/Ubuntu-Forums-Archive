---
title: "Small, distorted numbers"
date: 2005-06-02
forum: Desktop Environments
---

### Post by Reb on 2005-06-02
I'm having a problem now with my fonts - but only the numbers. They are much smaller than the rest of the text, and quite hard to read. I've attached a screenshot and my xorg.conf.

---

### Post by Reb on 2005-06-02
That is sf8sd9a8f8d. And the xorg.conf...
ps. I have the resolution set to 96 dpi and am using Bitstream Vera Sans. Bitstream Vera Sans Mono looks fine, as do all other evenly-spaced fonts. All unevenly-spaced fonts have the small numbers.

---

### Post by Reb on 2005-06-04
Anyone?

---

### Post by skoal on 2005-06-04
Howdy Mr. Gates!  I guess the fellers at Redmond can't help you out here, but maybe I can.

It looks like you're running at 1280x1024 like me.  Here's my relevant part from my xorg.conf:

        HorizSync       30.0 - 107.0
        VertRefresh     48.0 - 120.0
        DisplaySize     338 270 # for 1280x1024 (96x96)dpi

Our display size settings are fairly close.

I've got this in my /etc/fonts/local.conf file as well:

<match target="pattern">
                <edit name="dpi" mode="assign"><double>96</double></edit>
</match>

*** I used to have a very similiar problem like yours, although mine would manifest itself vertically, not horizontally (like yours).  When I made that DisplaySize change, it disappeared.

What happens when you try a different font like Verdana?  Do you have any MS TTF fonts installed?  Surely so.  If not, what would your buddy Ballmer say back at Redmond?

---

### Post by Reb on 2005-06-05
No change after those suggestions, no change using Verdana either. Attached is my ~/.fonts.conf and /etc/fonts/local.conf.

---

### Post by skoal on 2005-06-06
Hmm...

Have you tried turning off the "autohinter" completely?  I never use that thing, especially with MS TTFs - just medium or full.   Set that flag to "false" completely in your 'local.conf' file.  Here's mine for a reference:

---

### Post by Reb on 2005-06-07
I used yours, no go.

---

### Post by skoal on 2005-06-07
You'll have to turn off AA (anti-aliasing) in order for you to notice a difference with my settings - no AA, no autohinter, full hinting.

\\//_

---

### Post by Reb on 2005-06-09
Monkeying with all that stuff, no results and a lot of C-M-Backpsace

---

### Post by Reb on 2005-06-11
How can I completely purge all fonts and font settings, and start them over?

---

