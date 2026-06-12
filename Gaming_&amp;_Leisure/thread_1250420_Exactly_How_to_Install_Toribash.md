---
title: "Exactly How to Install Toribash"
date: 2009-08-26
forum: Gaming &amp; Leisure
---

### Post by JimBuntu on 2009-08-26
Add Toribash to your resources list by going to '**System>Administration>Software Sources**'. Click on the '**Third-Party Software**' tab then click '**Add**' at the bottom of that window. Then a smaller screen should pop-up asking you to '**Enter the complete APT line of the repository that you want to add as source**'. Copy and paste this line into the input area of that window:
```
deb http://linux.toribash.com/apt/ toribash/
```
Click '**Add Source**' when done. 

Now, go to your '**Terminal**' under '**Applications>Accessories**' and copy and paste this code:
```
wget -q -O - http://linux.toribash.com/sign.key | sudo apt-key add -
```
If you haven't already closed the '**Third-Party Software**' window, you can do that now. Let it reload too...

Lastly, go back to the '**Terminal**' and copy paste this code:

```
sudo apt-get install toribash
```

Type your password if needed. Then type 'Y' for 'yes' when it asks you if you are sure you want to proceed. 

That's it. The game should be listed in your '**Applications>Games**' menu. 

This is exactly what I did and it worked perfectly. I run 9.04 32bit.

If you end up wanting to remove it, use in '**Terminal**':
```
sudo apt-get remove toribash
```

Also, you will need to go back to the '**Third-party Software**' window as described above and remove the Toribash line you put in earlier.

---

### Post by Sealbhach on 2009-08-27
Why not just install using the debs from their download page?

[http://linux.toribash.com/](http://linux.toribash.com/)

.

---

### Post by 569874123 on 2009-09-06
Or you could use djl.

---

### Post by JimBuntu on 2009-09-08
Not everyone knows what your talking about. Hence the step-by-step.:)

---

### Post by Sealbhach on 2009-09-08
> **JimBuntu said:**
> Not everyone knows what your talking about. Hence the step-by-step.:)

Sorry, didn't mean to be rude, it was good of you to write that how-to, it just seems simpler to do it using the .debs.

.

---

