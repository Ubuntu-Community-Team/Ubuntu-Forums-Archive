---
title: "Weird KDE problems"
date: 2006-07-26
forum: Desktop Environments
---

### Post by reldruH on 2006-07-26
I recently switched my computer from Ubuntu to Kubuntu (did a clean install, didn't install KDE over Ubuntu) and since then I've been having some really weird problems. I'll click on software in the K menu and it will say loading on the bottom panel and the icon will start bouncing, but then it all disapears and the software never opens. This is happening specifically with KsCD and KAudioCreator. Other programs as well, but those are the ones I'm trying to open now. Any ideas?

---

### Post by aysiu on 2006-07-26
Paste this command in the terminal and paste the output back here: ```
kaudiocreator
```

---

### Post by ThrobbingBrain66 on 2006-07-26
I don't mean to hijack this thread, but I'm having the exact same trouble with Adept.  It usually takes 3 attempts to open. Here is the output from
```
kdesu adept
```

kapture::PkgSystem::PkgSystem()

adept: PackageDetails::setPackage()
adept: PackageInfo::setPackage()
adept: PackageInfo::setVersion() (valid)
adept: PackageDetails::notifyPostChange()
adept: PackageDetails::loadFileList()
ScimInputContextPlugin()
adept: PackageDetails::loadFileListWorker() entering loop
adept: PackageDetails::loadFileListWorker() leaving loop
adept: TagList: scheduling update
adept: TagList: scheduling update
adept: ExtendableList::updateExtenders(); count = 3
adept: ExtendableList::updateExtenders(); count = 0
adept: ExtendableList::updateExtenders(); count = 0
adept: ExtendableList::updateExtenders(); count = 3
adept: ExtendableList::updateExtenders(); count = 3
adept: rebuild running
adept: querying m_rangeProvider 0x84bc9a4...
adept: clearing...
adept: ExtendableList::clear()
adept: end of ExtendableList::clear()
adept: asyncCall to rebuildInsertRange...
adept: starting the thread...
adept: PackageDetails::updateLogical()
adept: PackageDetails::updateLogical: p = python-tclink p.component() = 0x8335af0
adept: rebuild running
adept: querying m_rangeProvider 0x84f5004...
python

python2.4-tclink

python

adept: clearing...
adept: ExtendableList::clear()
adept: end of ExtendableList::clear()
adept: asyncCall to rebuildInsertRange...
adept: starting the thread...
adept: ExtendableList::updateExtenders(); count = 3
adept: TagList (Tags I Want (drop tags here)): updating list
adept: TagList (Tags I Do Not Want (drop tags here)): updating list
adept: ExtendableList::updateExtenders(); count = 3

---

### Post by reldruH on 2006-07-26
> **aysiu said:**
> Paste this command in the terminal and paste the output back here: ```
kaudiocreator
```

Here's my output: ```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()

```

It hangs here. The command doesn't exit, the cursor just sits there blinking. Help?

---

### Post by missmoondog on 2006-07-27
looking all around for a solution to this same problem in several programs. k3b, in particular, on one machine. this machine, it's adept and synaptic.

---

### Post by missmoondog on 2006-08-04
> **reldruH said:**
> Here's my output: ```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()

```

It hangs here. The command doesn't exit, the cursor just sits there blinking. Help?


i get this message also, but mine is major opcode: 146

nobody has any ideas on this?

---

### Post by Neobuntu on 2006-08-04
I too am having Adept need to be clicked twice (or more) before it will give me the password dialog.

---

### Post by Bigglez on 2006-08-15
Yup. Me too. Adept 1 or 2 clicks before run. Gwenview will just stop opening after a while (I was up for 5days before the problems began to show).

This is my error on console:
Not sure it's related to these weird problems
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0

```

---

### Post by tlayton_at_work on 2006-08-15
I had been having trouble with one since I upgraded to Kubuntu Dapper.  Found a post somewhere to check /etc/X11/xorg.conf and comment out the "wacom" sections (since I don't own a wacom pad).  That just caused more failures.

Today, I uninstalled the xserver-xorg-input-wacom (which also uninstalled the xserver-xorg-input-all -- a metapackage so no problem).  Restarted the xserver, and stopped receiving those error messages. THe "wacom" sections still do show up in the xorg.conf.

BTW, my device opcode was 168.

Hope this helps.

---

### Post by tlayton_at_work on 2006-08-15
Actually, I misspoke on previous reply.  I started getting the errors after a fresh in of Kubuntu 6.06.  Just remembered that my ReiserFS partition bit it too much to fix, so I re-installed and and now using ext3.  Oh well, just more lost data.

---

### Post by missmoondog on 2006-08-18
have fixed my problem. did a clean install of ubuntu and graveman. burner works correctly now.

wonder what the issue was using kubuntu on this computer? everything pretty much worked right out of the box with kubuntu on my 6 other machines.

---

### Post by agrabah on 2006-08-18
I have the same issue with firefox... after I boot and run firefox for the first time the icon jumps around, but then firefox quietly disappears without opening. When I run it the second time it opens no prob.

The odd thing is that when running firefox my cpu usage does not seem to jump up, like nothing would be really loading...

Tine

---

