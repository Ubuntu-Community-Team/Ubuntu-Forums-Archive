---
title: "Evolution completely wrecked - help needed to recover [SOLVED]"
date: 2006-05-31
forum: Desktop Environments
---

### Post by stig on 2006-05-31
[This problem has been solved. See final message for solution]

Yesterday I posted a message in the Absolute Beginners' Forum about this problem but did not get any replies. Since then I have tried several things but Evolution is still completely unusable. I've searched Google and these forums but cannot find a solution. Perhaps someone in this forum can help me please?

The problem began yesterday when I clicked on a new mail message just arrived in Evolution. What I got was a warning: "The application "Evolution" has quit unexpectedly" and the options of "Restart Application", "Close", or "Inform Developers". Restart simply closed Evolution. When I opened Evolution again I got the same warning - and the same result on clicking either Restart or Close. Restarting the PC makes no difference. If I click outside the warning box it freezes the PC. At present I have no access to my mail.

If I start Evolution in the terminal I get the same result and in terminal it shows:

adding hook target 'source'

(evolution:7993): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:7993): GnomeCanvas-CRITICAL **: gnome_canvas_request_redraw: assertion `GNOME_IS_CANVAS (canvas)' failed
evolution: tif_jpeg.c:1505: JPEGCleanup: Assertion `sp != 0' failed.

To make sure I kept my mail, I backed up .evolution and .gconf/apps/evolution. Then I did a reinstall of Evolution...but still had the problem. So then I did a complete removal followed by installation of Evolution...but still got the warning message.

Next I deleted the .evolution and .gconf/apps/evolution folders. When I next opened Evolution there was no warning message and it would work but I had no mail and no custom folders.

If I add back the original .gconf/apps/evolution folder only the result is the same - no warning message but no mail and no custom folders.

If I add back the original .evolution folder only I get my mail and custom folders but also the warning message and the problem again.

I don't understand enough about Linux to know what to do next - I'd be grateful if someone could please help me get my Evolution back in working order.

---

### Post by stig on 2006-06-05
Having not had any solution to this problem through the Ubuntu forums, I posted on the Evolution Mailing List. After some correspondence, it emerged that the problem was due to a specific email with attachments. Once this email was removed the problem was solved. A copy of the email has been passed to Evolution developers and work is continuing to determine why it crashed the software. Some similar experiences have been reported by others.

For details of the solution to the immediate problem, see the section titled:

"Recovering from a mail causing Evo to crash"
on the web page:

[http://mail.gnome.org/archives/evolution-list/2006-June/msg00063.html](http://mail.gnome.org/archives/evolution-list/2006-June/msg00063.html)

---

