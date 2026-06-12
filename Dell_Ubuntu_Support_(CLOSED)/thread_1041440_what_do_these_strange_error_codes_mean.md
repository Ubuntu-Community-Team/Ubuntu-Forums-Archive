---
title: "what do these strange error codes mean??"
date: 2009-01-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BertP on 2009-01-16
I have just finished trying to upgrade to Ubuntu 8.04 for the 3rd time!  each time I have ran into these same strange error messages on initial restart and sometimes in other cases!  last night I ran Dell's memory check and extended system check and all the hardware seem to be ok.  One further complication is that I am using an using a very old Dell 15 inch LCD monitor and immediately before these messages I get a "video mode not supported" message, so there may be further diagnostics that I may be missing before the video mode changes to a mode my monitor supports. 

Anyway the messages are basically 3 lines repeated over and over, 
during startup; another 3 popping out perhaps every 20 or 30 seconds
seemingly repeating infinitely once they start.
---------------------------------

[ 320.450198 ] ata2:00 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

[ 320.450198 ] ata2:00 cmd a0/00:00:00:24:00/00:00:00:00:00:/a0 tag 0 pio 36 in

[ 320.450198 ] ata2:00 status { DRDY  }
--------------------------------------------------------------------
the 3 digit+6 decimal numbers in the first field start  low and keep incrementing, the other columns seem to repeat over and over, though, to be honest,  I have not watched the messages closely for more than short period

If anyone needs it I can try to describe in more detail circumstances in which these messages appear.  I am really concerned about whether I should keep 8.04 are revert to the version that shipped with my computer last January

---

### Post by BertP on 2009-01-16
I checked again and  it appears that these error messages are being displayed through BusyBoy v.1.13 and apparently these are initramfs errors because that name appears at the very beginnning of the error list.

The most consistent way I can actually bypass these error messages to load ubuntu is to choose the boot menu, choose the utilities and then exit to load ubuntu.  Is all this  indicative of a hardware problem?

---

