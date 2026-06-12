---
title: "Unity 2D displays garbled fonts for menus, contextual, url etc"
date: 2012-10-21
forum: Desktop Environments
---

### Post by PikoMedia on 2012-10-21
Hi,
I've got this crippling problem since I ran sudo apt-get update two days ago on my Ubuntu 12.04 setup. In Unity 2D, menus, contextual info, urls, file content are all "garbled" and hardly intelligible. 

Refer to the attached screenshots:
- simple text doc opened with gedit: even the file contents is screwed up
- Three tabs of Chrome open, displaying the problem in the tab titles and the url

Performing simple doc operations or even surfing the web becomes a real pain, need I say? 

Any ideas? Any logs I can pull to clarify this further? I know when this hapened, so if someone can point me in the right direction I could get the logs from the update that seems to have caused the problem.

Some platform details (not that I believe it has an influence, but then again):
Asus Zenbook Prime UX31A 4003X

Thanks

---

### Post by PikoMedia on 2012-10-21
Even the terminal is screwed up!
I went to look in the /var/log/dpkg.log to see what was installed on Oct 19. It turned out there were appx 400 entries, of which 125 vere installed packages. There were 280 "half-installed" (no idea what that means. Normal?).
Attached a file containing 'cat dpkg.log | grep 10-19 | grep installed'.
Any thoughts?

---

### Post by vasa1 on 2012-10-21
> **PikoMedia said:**
> Hi,
I've got this crippling problem since I ran **sudo apt-get update** two days ago on my Ubuntu 12.04 setup. ...
Is that all you did?
If I understand correctly, it should have absolutely no impact. Did you by any chance also do a dist-upgrade?

---

### Post by PikoMedia on 2012-10-21
All I did was
[FONT="Courier New"]sudo apt-get update[/FONT]
(Check the update log in my previous post)
No dist update. I'm still running 12.04
[FONT="Courier New"]lsb_release -r
Release 12.04
[/FONT]

I'm clueless... Any ideas on where I can start investigating?

---

### Post by PikoMedia on 2012-10-25
New observation:
the title field for open applications is transparent (refer to the attached screenshot). Something's really f-ed up here...

---

### Post by Bashing-om on 2012-10-25
PikoMedia; Hi !

From this "There were 280 "half-installed" (no idea what that means. Normal?)." submitted in earlier post...indicates a crippled system.
I recommend repairing the  file system, see if that indeed resolves the graphics situation.

I do this by inspecting the errors that apt-get generates. 
Post the output from terminal commands:
```
sudo apt-get update
sudo apt-get upgrade
```following the leads that apt-get generates to repair the "half installed" packages.
[INDENT][INDENT]try'n to help <==BDQ
 
[/INDENT][/INDENT]

---

### Post by PikoMedia on 2012-10-27
Hi Bashing-om,
The output from sudo apt-get update & sudo apt-get upgrade is in the attached files. I didn't see anything very probing there, but perhaps your eyes are sharper than mine.
If nothing comes up, I'll probably just have to reinstall from scratch (which feels a bit like defeat, I must admit).
Thanks

---

### Post by PikoMedia on 2012-10-27
Finally the issue has disappeared! It's impossible to say exactly what fixed it, but then again it's not an exact science.
Basically, I ran apt-get update & apt-get upgrade, rebooted once, still no progress, dispaired, read som jokes on the web, rebooted a second time and then shazam!, the garbled text was gone.
Beats me, but if my system is operational it's good enough for me.
Thanks Bashing-om for your help!
Cheers
Tom

---

### Post by Bashing-om on 2012-10-27
PikoMedia;

It is pleasing that the system is stable. Yeah, it would be gratifying  to know what fixed the situation; Mark it up to a smart operating system, huh ???


[INDENT]all's well that ends well <== BDQ


[/INDENT]

---

