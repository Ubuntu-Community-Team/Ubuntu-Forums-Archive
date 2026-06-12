---
title: "On Remote Server, Nautilus sometimes can't create folders/files"
date: 2009-04-14
forum: General Help
---

### Post by xareck on 2009-04-14
I've only been able to test this with GDM, Nautilus environments, so this may exist on others.

Some background:
2 servers. 1 development box, 1 production box.

I have 3 users on each: "www-data", "auk100" & "first", "auk100" is in "first's" group. We have a folder called "www" that has an owner of "www-data" with a group of "first"

**Production:**
```

$ id www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data)

$ id auk100
uid=1001(auk100) gid=1000(first) groups=1000(first)

$ id first
uid=1000(first) gid=1000(first) groups=1000(first),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),111(lpadmin),112(sambashare),113(admin)

$ ls -la
drwxrwxr-x 46 www-data first       4096 2009-04-14 13:09 www

```

**Development:**
```

$ id www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data)

$ id auk100
uid=1001(auk100) gid=1000(first) groups=1000(first)

$ id first
uid=1000(first) gid=1000(first) groups=1000(first),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),111(lpadmin),112(admin)

$ ls -la
drwxrwxr-x 13 www-data first  4096 2009-04-14 16:55 www

```

Now, I've even gone so far as to duplicate this problem on a fresh new machine and basically it is as follows. 

Seeing as how the production and development boxes above essentially mirror each other in terms of access and permissions. If I use Nautilus's "Connect to Server" functionality and connect to both machines (as auk100), when I right click in the Production's www folder, I can create folders and files. If I attempt to repeat this on the Development server (or the new test box), both of those options are grayed out.

I've been tearing my hair out throughout the day trying to understand why it works perfectly fine on one server, and yet on another (and even another test machine), it does not want to allow me to create files.

If anyone can provide insight/help, I'd be eternally greatful.

Thank you,

Arun U. Kapil

---

### Post by xareck on 2009-04-15
Any ideas?

---

### Post by Brucevdk on 2009-04-18
I stumbled upon this while searching for interesting Nautilus questions I could answer. If you're connecting over SFTP (which I assume you are) this might be related to a [GVFS issue that was recently fixed](http://bugzilla.gnome.org/show_bug.cgi?id=559902) (two days ago) by Alexander Larson (lead developer of, among other projects, Nautilus). 

Alex explained the issue to me over IRC (edited for clarity):

> 
<Brucevdk>	 Hmm, so Nautilus not being able to handle directories over SFTP with ACLs is probably a GVFS issue (e.g. no support for this)?
<alex_>	 in what sense is it not handled?
<alex_>	 i mean, gvfs has no way of knowing of the acls over sftp, its just not in the protocol
<alex_>	 however, they should be enforced by the OS on the server
<Brucevdk>	 alex_: [http://bugzilla.gnome.org/show_bug.cgi?id=559902](http://bugzilla.gnome.org/show_bug.cgi?id=559902)
<bugbot>	 Bug 559902: normal, Normal, ---, [email]nautilus-maint@gnome.bugs[/email], UNCONFIRMED, Nautilus doesn't seem to support ACLs over SFTP
<alex_>	 so, nautilus grays out some operations?
<Brucevdk>	 alex_: indeed
<alex_>	 Basically, what should happen here is that the gvfs backend has no way of determining whether it has permissions for something ahead of time
<alex_>	 so it will not set any of the access:can_write etc attributes
<alex_>	 and nautilus, on seeing those unset should not threat it as if they are FALSE
<alex_>	 need to figure out where this goes wrong though
<alex_>	 Ah, i see
<alex_>	 g_file_info_set_attribute_boolean (info, G_FILE_ATTRIBUTE_ACCESS_CAN_READ,
<alex_>	 perm & 0x4);
<alex_>	 g_file_info_set_attribute_boolean (info, G_FILE_ATTRIBUTE_ACCESS_CAN_WRITE,
<alex_>	 perm & 0x2);
<alex_>	 g_file_info_set_attribute_boolean (info, G_FILE_ATTRIBUTE_ACCESS_CAN_EXECUTE,
<alex_>	 perm & 0x1);
<alex_>	 total bogus
<Brucevdk>	 alex_: oh btw, I might file a new bug for this. If you have a directory set to root:some_shared_group and with permissions 770 and you open that directory as one of the users from some_shared_group the options to write are still grayed out
<Brucevdk>	 oh wait, same issue
<alex_>	 its the same yes
<alex_>	 but in general permissions and things like that on sftp are hard
<alex_>	 the servers uid/gid mappings are not the same as the local ones
<alex_>	 so, we don't know e.g. what groups we are in
<Brucevdk>	 alex_: so basically, something like the command line sftp also doesn't actually try to figure out the permissions but just tries it and then sees if the operation fails or didn't?
<alex_>	 its only by stat:ing the login directory we're able to guess our own uid in fact
<alex_>	 Brucevdk: yeah 


So the issue does not only occur with ACLs as the subject of the issue linked above indicates but also with permissions that trickle down from the group (as seems to be the issue in your situation), as it seems there is no proper way to figure out the groups a user belongs to. As you can see GVFS would incorrectly return FALSE for all permissions, this has now been fixed.

So hopefully this fix will be included in Jaunty, if you want to make sure it might be best to open a bug on Launchpad. Otherwise you should be able to manually grab GVFS from SVN/Git and install it manually.

Good luck and let me know if it worked out for you.

---

