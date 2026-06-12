---
title: "update-manager &amp; login user icons"
date: 2006-03-25
forum: Desktop Environments
---

### Post by v4169sgr on 2006-03-25
I couldn't find the exact analogue to the answers I was seeking on the forums, so have decided to post a question now.

I am presently trying out Kubuntu [based on Breezy or 5.10] on a second machine as a target for migration from my primary resource which is SuSe 9.1 using KDE.

I'd downloaded a March 2006 version of the kubuntu [Breezy] iso image, burned to disc, and installed over a previous attempt using edubuntu with gnome.

I'm afraid I haven't taken to Adept, hence one of the first things I did [after updating the install] was to install Synaptic and use that instead.

I'd also got used to the gnome update-manager which I believe is tied in to Synaptic. I found this very useful indeed. I've heard rumours that update-manager could be persuaded to work in KDE, but have not yet managed it myself. Any clues?

Second question: my target audience on SuSe 9.1 are conditioned to a login environment in which they can click on an icon representing their user, and their username field will be filled in. Although I notice I can choose a login icon per user in the KDE Control Center as usual, the login icons seem to be disabled. What can I do to ensure the users have a similar experience to that which they are getting in SuSe 9.1?

Any assistance is gratefully appreciated!:cool:

---

### Post by v4169sgr on 2006-03-26
Looks like I've got something to learn about attention-grabbing posts:rolleyes: The least number of views on the entire page:-k :D 

So, questions again, hopefully clearer:

1. I like synaptic, not adept. How can I get update-manager working in KDE?

2. How can I get clickable login pictures as in SuSe on Kubuntu?

Thanks!8)

---

### Post by lowey23 on 2006-03-27
This is probably not a great help to you, but I didn't want you to think everyone was ignoring you. I use synaptic for adding or removing packages and the command line apt-get thingy for updates. I didn't like adept much. The updater seemed to work OK but didn't seem to tell me what it was doing, just added and removed things and said "there you are, Lowey, we know whats best for you and we did it".
The command line update/upgrade lets you know whats happening and is a nice simple tool to use.

Just my 2cents.

Cheers

Lowey

---

### Post by v4169sgr on 2006-03-27
Thanks very much Iowey23 :cool: Your support is appreciated.

I am getting the impression that the behaviour of Adept seems to be somewhat 'un-Ubuntu': I agree that Synaptic suits my needs just right, and neither assumes too little or too much. However a little KDE integration would be niiice ....:mrgreen: 

What I have found is that starting the update-manager from bash with

```
$ update-manager &
```

not one, but TWO empty squares appear in the applet area on the KDE taskbar. These disappear when update-manager is killed.

I really wish someone could help me with this as I miss having an update manager very much :( The YaST update manager in SuSe works file, and the Gnome integration of update-manager in Ubuntu works a charm [though a little on the intrusive side sometimes!] and I can just tell I'm gonna miss seeing updates notified:( 

On the login icons front, this mystery has so far resisted all my efforts ](*,) I thought that the key was in the login manager set up in the KDE control centre, but it doesn't seem to matter what I do, I just can't get the darned things to appear on the login screen! SuSe does it nicely, why can't Ubuntu?? I thought it might be a matter of a KDM theme [from kdelooks.org] but that doesn't seem to help either.

If no-one helps soon, I shall threaten you all with an attempt to write a solution myself :twisted: 

Thanks again for any support or help!

---

### Post by v4169sgr on 2006-04-02
I've since worked out that what I am really looking for is a faces theme. I've 'solved' this problem in the meantime by using GDM to log into KDE, and have set up human-list from gnome-look.org.

Any recommendations for a nice KDM faces theme?

Thanks!

---

