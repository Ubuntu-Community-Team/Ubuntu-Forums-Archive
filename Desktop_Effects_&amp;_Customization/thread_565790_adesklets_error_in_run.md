---
title: "adesklets error in run"
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by Chymera on 2007-10-02
after installing adesklets, when running the adesklets installer i get the following output > &#9474;Retrieving data online... OK                                                  &#9474;
&#9474;Checking locally installed desklets... OK                                     &#9474;
&#9474;Downloading asimpleimage desklet... OK                                        &#9474;
&#9474;Verifying download integrity... OK                                            &#9474;
&#9474;Opening the downloaded archive...                                             &#9474;
&#9474;!!! An error occured during the operation !!!                                 &#9474;
&#9474;Traceback (most recent call last):                                            &#9474;
&#9474;  File "/usr/bin/adesklets_installer", line 223, in run    

so, whats wrong with the file? why wont it work?

---

### Post by Chymera on 2007-10-14
bump...

---

### Post by Gourgi on 2007-12-12
i get the some errors too :(
and i van;t use adesklets 
```
&#9474;Retrieving data online...                                                     &#9474;
&#9474;!!! An error occured during the operation !!!                                 &#9474;
&#9474;Traceback (most recent call last):                                            &#9474;
&#9474;  File "/usr/bin/adesklets_installer", line 208, in run                       &#9474;
&#9474;    self.desklets.run()                                                       &#9474;
&#9474;  File "/usr/bin/adesklets_installer", line 108, in run                       &#9474;
&#9474;    ).getElementsByTagName('entry')]])                                        &#9474;
&#9474;  File "/usr/bin/adesklets_installer", line 81, in extract_tag 
```

anyone knows what's wrong ?

---

### Post by mwiertz on 2008-03-01
bump, same error here... :(

does anyone know how to solve?

thanks a lot in advance

---

### Post by stedevil on 2008-03-05
Ok, we have 2 separate issues in this thread but all of you are pastiing only HALF the error output message (most importantly the actual error). Use TAB and then arrows to scroll up/down in the "log" window.

In any case, I'm seeing the following error
> 
&#9474;Retrieving data online... &#9474;
&#9474;!!! An error occured during the operation !!! &#9474;
&#9474;Traceback (most recent call last): &#9474;
&#9474;  File "/usr/bin/adesklets_installer", line 208, in run &#9474;
&#9474;    self.desklets.run() &#9474;
&#9474;  File "/usr/bin/adesklets_installer", line 108, in run &#9474;
&#9474;    ).getElementsByTagName('entry')]]) &#9474;
&#9474;  File "/usr/bin/adesklets_installer", line 81, in extract_tag       
&#9474;    for tag in ('title', 'link', 'generator')] &#9474;
&#9474;IndexError: list index out of range &#9474;
&#9474;                                                               


I presume it's some dependency that is incompatible. Googling for a solution myself right now.

Closest so far is this Gentoo bug. Fully updating the system fixed it for him (exactly what package fixed it it doesnt say however).
[http://bugs.gentoo.org/show_bug.cgi?id=200704](http://bugs.gentoo.org/show_bug.cgi?id=200704)

---

### Post by stedevil on 2008-03-05
Ok, seems that the error was actually on the server feed end. It's fixed now by adesklets coder, Sylvain. Happy adesklets -i everyone :)

---

### Post by Dasani on 2008-03-08
hmm....I had given up on adesklets not being able to do anything for me! until I heard about this 'fix'.
Now adesklets_installer doesn't give me the regular error in the info box as it did, but now I get this:

Traceback (most recent call last):
  File "/usr/local/bin/adesklets_installer", line 632, in <module>
    if globals()['%sGUI' % ui](): break
  File "/usr/local/bin/adesklets_installer", line 590, in cursesGUI
    return _cursesGUI()
  File "/usr/local/bin/adesklets_installer", line 288, in __init__
    self.run()
  File "/usr/local/bin/adesklets_installer", line 529, in run
    curses.wrapper(self._run)
  File "curses/wrapper.py", line 44, in wrapper
  File "/usr/local/bin/adesklets_installer", line 560, in _run
    dpad.refresh(self.driver.desklets.descriptions())
  File "/usr/local/bin/adesklets_installer", line 70, in descriptions
    for k, v in self.iteritems()]

Anyone have an idea as to what I can do to fix this?

---

