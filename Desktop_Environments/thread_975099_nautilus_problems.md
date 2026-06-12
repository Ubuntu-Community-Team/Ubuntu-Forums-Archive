---
title: "nautilus problems"
date: 2008-11-08
forum: Desktop Environments
---

### Post by sonyboy on 2008-11-08
hi all, i have the following problem:when i try to run nautilus as root i get those errors: 


root@Tea-House:/home/strumf# nautilus
seahorse nautilus module initialized

(nautilus:6465): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6465): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:6465): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6465): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault


but all things works great when i run nautilus as a user.Can anyone figure out what is the problem?

thanks in advance!

---

### Post by chitowner on 2008-12-17
I am having identical problem on my hardy install. I know nautilus was working after I did a clean install but have no idea what happened in the meantime. I used apt-get to remove and re-install nautilus, but the problem persists. 

comment here: i much prefer nautilus over dolphin and that is why this is an issue for me. i do use konq as both a file and web browser but nautilus is much preferable when viewing in icon mode. dolphin is not apparently able to make tabs. IMO that's a severe constraint to how i work.

Hopefully *somebody* out there will respond. I know from what I found via Google that others have this problem with nautilus. I have not found a solution anywhere, or even a good comment on what the cause might be.

If anyone knows how to discriminate whether this might be a bug, do chime in. That might be helpful.

PS: Digging further this appears *not* to be a nautilus-specific problem, but is due to "GLib" called by a variety of apps.

SOLUTION: CHECK YOUR OPTICAL DRIVE!
[https://bugzilla.redhat.com/show_bug.cgi?id=458586](https://bugzilla.redhat.com/show_bug.cgi?id=458586)

I knew I had a blank DVD in the burner. It's been there for several reboot cycles and I was planning to use it for a folder backup. Opening the drive lets nautilus boot without problems.

I SUGGEST THIS IS A BUG in GLib.

---

