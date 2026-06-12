---
title: "Can't resize Linux window on Hyper-V"
date: 2022-10-26
forum: Desktop Environments
---

### Post by leolevosky on 2022-10-26
Hi,

I have followed the instructions I found elsewhere on how to resize the window of a Linux guest on Hyper-V. These say:

Launch a terminal window and then edit the /etc/default/grub file using your favourite editor:

**sudo nano /etc/default/grub**

Find the GRUB_CMDLINE_LINUX_DEFAULT entry and modify the entry to:

[B]GRUB_CMDLINE_LINUX_DEFAULT="quiet video=hyperv_fb:1920x1080"

I have used this method before on Linux Mint but on Lubuntu it makes no difference.

Can anyone please tell me why and how to fix this?

I have been advised to use Virtualbox but that runs really slowly on my machine and I have a number of other Hyper-V VM's

Thanks.
[/B]

---

### Post by MAFoElffen on 2022-10-26
Sort of... Except Ubuntu will not recognize that driver. I have never seen that driver before... And I support the Linux Graphics Layer for over a decade now... Please provide a link to that please, so I can review that.

In the meantime, changing these lines
```

GRUB_CMDLINE_LINUX_DEFAULT="-- quiet video=fbvesa:mode_option=1920x1080-32,mtrr=3,scroll=ywrap"

GRUB_GFXMODE=1920x1080x32

```

Then after saving it
```

sudo update-grub

```

---

### Post by ActionParsnip on 2022-10-28
What are you doing on the VM that needs such a large display? What resolution are you using presently? Is it a desktop based OS or server based? If you manage the VM in a terminal then just SSH to the VM and use PowerShell / PuTTY on the local PC (Easier)

---

### Post by leolevosky on 2022-10-29
I finally got around to trying what you said and it made no difference.

When you asked me to provide a link. A link to what? The information I provided in the post is the only information I have. I've no idea where it came from. I emailed it to myself and it worked on Linux Mint previously. Now I cannot get it to work.

I'm sure if you search for the commands you will find the original post but I have no idea where I found it.

---

### Post by leolevosky on 2022-10-29
Large display? Not at all just larger than Hyper-V gives me by default.

If I were using commands I would happily use PuTTY but I'm using a desktop Linux and so want a reasonable size desktop

---

