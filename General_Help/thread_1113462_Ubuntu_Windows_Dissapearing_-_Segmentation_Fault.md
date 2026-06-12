---
title: "Ubuntu Windows Dissapearing - Segmentation Fault?"
date: 2009-04-01
forum: General Help
---

### Post by Andysan on 2009-04-01
Hi community,

I've recently been experiencing issues with windows dissapearing.  I'm a fan of magic, but this is not cool.  MY Software Sources window dissapears when i click the "Import Key File" button on "Authentication" tab.  Similarly, my "Login  Window" tool closes as soon as i open it.  System log reads as follows:

```
Apr  1 23:25:51 *****LINUX kernel: [  185.726490] software-proper[6226]: segfault at 00000004 eip b677aaa0 esp bfff6b50 error 4
Apr  1 23:31:33 *****LINUX kernel: [  527.905936] software-proper[6344]: segfault at 00000004 eip b676eaa0 esp bfb37e90 error 4
```

Furthermore, when i run the Sources app from a prompt, i get the following when the window closes:

```
(software-properties-gtk:6414): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed
sys:1: Warning: g_error_free: assertion `error != NULL' failed

(software-properties-gtk:6414): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(software-properties-gtk:6414): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
http://ubuntuforums.org/showthread.php?t=849418

```

[I believe that this person has the same issue]("http://ubuntuforums.org/showthread.php?t=849418"), but much Googling can find me no resolution, other than to use the command prompt instead to add sources, which is not a solution IMHO.

EDIT - I'm using Hardy btw, and the only changes that i have made recently is to install Gnomad2 and add the Wine repository to my sources.

Thanks.

---

### Post by Andysan on 2009-04-01
If anyone else is suffering from this, try taking any blank CDs outta your disk drive.  Oddly enough this fixed it.  I was aware that my writer was on its way out, but not that it could affect apps such as Software Sources of Login Window.

I am still interested as to why this is happening please - I'm reading up on segmentation faults and most threads relate to people having issues reading from a CD - i cant understand why it would affect anything that doesnt use the drive.

I guess my PC isnt likely to fall over or anything, i cant be bothered to take the drive out right now.

Cheers.

---

### Post by jms1989 on 2009-04-09
I an finding the same problem but mine seems to revolve around ktorrent. Sometimes it runs fine but there are times it will just close on its own even if I happen to be using it at the time. It ran perfectly on my old pc and when running from my old ide disks so my problen seem to lie in my sata drives because sometimes I'll see a I/O error report when accessing a sata drive, including my two sata burners.

---

### Post by Andysan on 2009-04-09
Maybe its an indication that one of your drives is about to give up.  My disk drive has since given up the ghost entirely, so make sure that everything is backed up!

---

### Post by jms1989 on 2009-04-10
That would make since if my hdds were over 6 years old. I've only had'em for a month or so. The two 500s were manufatured in January 09 and my 1TB was manufatured in Febuary of the same year.

After removing all but one and replacing the main ram module with one of the others, my file transfers seem to work ok and ktorrent has yet to seg fault. I will give my other modules a test tomorrow and after I come back from my trip for three days. After a days work with each module and if they prove that they work ok, I'll add all the good ones. When I took out the one that was causing problems and replaced it with another everything was fine.

I'm beginning to wonder how to get a replacement for a single faulty ram module out of a 2 pack. ??? Hmm...

---

### Post by Andysan on 2009-04-10
Aren't HDD's likely to either break either within the first few months, or years later?  I hope hat you are able to trace the fault and that it doesnt prove too costly!:confused:  Keep us posted.

---

