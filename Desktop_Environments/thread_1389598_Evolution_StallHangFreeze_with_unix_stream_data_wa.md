---
title: "Evolution Stall/Hang/Freeze with unix_stream_data_wait in the System Monitor"
date: 2010-01-24
forum: Desktop Environments
---

### Post by VitalBodies on 2010-01-24
**Evolution Stall/Hang/Freeze with unix_stream_data_wait in the System Monitor?** 
I have been having the issue of Evolution (Email Client) going blank/grey. 

If I reconnect to the internet (even though I am connected) the program unfreezes. But I have to log in and all that so it is a hassle. This happens many times a day. 

Ubuntu Koala (64-bit) and whatever version of Evolution shows up in the normal updates when Ubuntu updates the system from the MAIN SERVER. 
System Monitor (processes tab) shows unix_stream_data_wait when the freeze is happening. I have Evolution set to POP email. 

GBT (back trace) shows a broken pipe. 

I did quite a bit of searching on this but could not find an answer or work around. 

A complete re-install of Evolution or Ubuntu did not help. 

Lenovo D10 ThinkStation 8-way 18GB ram and Nvidia Card. 
I did not have this issue on a one processor Q6600 quad core computer with the exact same hard drive/ubuntu plugged in but I do on the my system with TWO quad core Xeon processors? 
A  fresh install with fresh hard drive did not help.   
I am using Firestarter firewall.

Here is some more info in case this helps:
Bug Report: [https://bugzilla.gnome.org/show_bug.cgi?id=606149](https://bugzilla.gnome.org/show_bug.cgi?id=606149)
Comments: [http://www.uluga.ubuntuforums.org/sh...87&postcount=7](http://www.uluga.ubuntuforums.org/sh...87&postcount=7)

---

### Post by VitalBodies on 2010-01-24
Not really sure how to go about finding the answer?

---

### Post by VitalBodies on 2010-01-24
Is there a known place for documentation, faq or other resource for this kind of problem? I tried Gnome web site but did not find a solution.

---

### Post by VitalBodies on 2010-01-26
I have seen online that there are a number of folks with this issue. 
So what are the clues? 
If Evolution thinks it has lost the connection the whole program (shell?) freezes. Not just the part that shows the inbox but even a separate window you might be replying to a message in. 
So what does this really say? 
I got rid of the NOTIFICATION icon so that is not the issue. 
I am still connected and can load pages in Firefox so it is not really the connection, although the connection might be *intermittent*. 
I would guess that this issue is two things: 
The problem is at the unix level. 
...And.
Evolution is not the issue itself, but is not compensating for the issue properly. 
Yet...
Yet this is that only happening if the issue with unix is NOTED on one processor while Evolution is on another processor since this happens only on a TWO cpu system? 

Another possibility is that the connection is fine but the delay is with the email server - I would still guess the same guess.

What is your best guess?

---

### Post by VitalBodies on 2010-01-29
Is there a way to know when the connection goes down? 
I know that the icon up in the corner of the screen will show if the connection TOTALLY goes down but what about if there is just something intermittent and temporary and does not bring the whole connection down?

---

### Post by VitalBodies on 2010-03-10
So far I think this issue might be related to the keys or key rings. If I open this: 
Applications > Accessories > Passwords and Encryption Keys 
Evolution unfreezes. I still have to dis-connect/reconnect form the net to download the mail though, and yes, Evolution will ask for the password. It seems evolution keeps forgetting the key?

I deleted the key and eveloution recreated one but that did not help. It seems to be missing a group key?

---

### Post by VitalBodies on 2010-03-10
Evolution hangs at this message: 
```
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-Mail'
```

How would I add that group Passwords-Mail? 
I looked over this: 
Applications > Accessories > Passwords and Encryption Keys
Which I think is called seahorse but my mind was not flooded with insight even after reading the docs twice.

---

