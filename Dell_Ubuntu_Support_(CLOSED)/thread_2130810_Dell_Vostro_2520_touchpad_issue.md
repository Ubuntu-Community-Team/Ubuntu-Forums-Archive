---
title: "Dell Vostro 2520 touchpad issue"
date: 2013-03-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Endsetzliche on 2013-03-30
Greetings.

I bought this laptop in January. Everyone once so often, randomly occurring, the touchpad suffers severe cursor control issues. When this happens the cursor does not go to where I gesture it with my finger. In this state the cursor can even move on its own slightly (nothing is touching the touchpad). Restarting seems to fix the issue. It's quite frustrating as it's already caused some lost work. I've contact Dell about this, but they apparently don't support ubuntu, and instead pass the buck off to canonical. I'm a bit of bit of a novice with Ubuntu. If this was a windows PC I'd replace/update the touchpad driver. This was suggested to me by a dell rep. I don't know how to update the touchpad driver in ubuntu. I have searched for instructions but I haven't found anything definitive that will help me with this issue. Right now the laptop is running 12.04. Would updating to 12.10 fix the issue? I was considering installing linux mint as I've heard good things about it, but considering it's debian/ubuntu based, I'm not sure if that would actually fix the issue or not.

Doing some more searching about this, I've heard that it might be a "flea power" issue? I've never had this issue with other laptops before.

---

### Post by mikewhatever on 2013-04-01
Can you post the output of **xinput list**. It should show how the touchpad is recognized, and might provide something to search for. I've seen reports of poor support for Alps and Elantech touchpads, perhaps you have one of these. Newer software usually provides better support for newer hardware, but I'd advise running 12.10 from CD/USB to test first.

---

### Post by Endsetzliche on 2013-04-01
Thanks for the reply Mike. I'm not exactly sure how to set a list all parameter for that command, even after looking at the man page. Here's the output for xinput --list (which is the same output for xinput with no switches):

> xxx@xxxxx:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                             id=12    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad            id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_HD                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)]

Looks like it is an Alps touchpad, which likely explains why it occasionally acts wonky. Is there a way I can update the driver for the touchpad? I do plan on updating to 12.10 if I can't find a simpler fix for this issue.

---

### Post by mikewhatever on 2013-04-01
I don't know how to update just the touchpad driver, and am not sure it would help in your particular case. Apparently, that machine has been certified for Ubuntu 12.04, and searching doesn't turn up similar problems with Vostro 2520.

---

### Post by Endsetzliche on 2013-04-02
I spoke to a Canonical rep this morning, and he mentioned the same thing about certification. He did however mention that any minor updates afterwards may have broken something. I might post a critical update post on launchpad, as the Canonical rep mentioned. Ultimately I might just install 12.10 and see if that helps.

---

