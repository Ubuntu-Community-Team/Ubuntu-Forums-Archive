---
title: "Will this be a problem later on?"
date: 2007-09-03
forum: Desktop Effects &amp; Customization
---

### Post by ZeldaFan on 2007-09-03
After trying to sudo apt-get update, I get this dealing with not being able to find a key or something like that with Trevino's repository for Compiz Fusion. Will this hinder me in the future to get updates to CF or am I supposed to recieve such results. This is what I get (in addition to the rest of the output that doesn't concern CF): 
```
W: GPG error: http://download.tuxfamily.org feisty Release: The following signat
ures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems

```

---

### Post by Happy_Man on 2007-09-03
It won't stop you from getting upgrades, it's just Ubuntu's way of saying, "I have no idea if these packages are credible, so don't blame me if your computer blows up." Of course, that will never happen. Don't worry.

---

### Post by thelocust on 2007-09-03
[FONT=Arial]enter this in terminal

[/FONT][FONT=Arial]```
KEY=DD800CD9; sudo gpg --keyserver subkeys.pgp.net --recv $KEY && sudo gpg --export --armor $KEY | sudo apt-key add -
```

I got it [here]("http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository")[/FONT]

---

### Post by FuturePilot on 2007-09-03
Then you'll need to run
```
sudo apt-get update
```

---

### Post by ZeldaFan on 2007-09-03
Is that key previously posted for the trevino repository? That's the repository I've used before to install it.

---

### Post by FuturePilot on 2007-09-03
Yes, that's for Trevino's repository.

---

### Post by ZeldaFan on 2007-09-03
Okay, well I just copy and pasted the code to get the key. Here's the output if its relevant at all:
```
gpg: directory `/home/rohan/.gnupg' created
gpg: can't open `/gnupg/options.skel': No such file or directory
gpg: keyring `/home/rohan/.gnupg/secring.gpg' created
gpg: keyring `/home/rohan/.gnupg/pubring.gpg' created
gpg: requesting key DD800CD9 from hkp server subkeys.pgp.net
gpg: /home/rohan/.gnupg/trustdb.gpg: trustdb created
gpg: key 81836EBF: public key "Treviño (3v1n0) <trevi55@gmail.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

```

After sudo apt-get update, I still get the same results.

---

### Post by ZeldaFan on 2007-09-03
which means that there's still a gpg error...

---

### Post by ZeldaFan on 2007-09-03
Oh, wait, I seem to be mistaken. After another couple sudo apt-get update 's, it seems to be working fine. Now when ever I sudo apt-get update it all is working normally, I didn't no why it didn't work initially though.

---

### Post by FuturePilot on 2007-09-03
I think the command should be
```
sudo gpg --keyserver subkeys.pgp.net --recv $KEY && sudo gpg --export --armor $KEY | sudo apt-key add -
```

---

### Post by thelocust on 2007-09-03
my bad copied a little to much.

---

