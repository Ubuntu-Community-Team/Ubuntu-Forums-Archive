---
title: "Error with Update Manager"
date: 2009-06-04
forum: Desktop Environments
---

### Post by AmpersUK on 2009-06-04
**Error reads:** "Error failed to fork pty"

I get the above error message when I try to update my 9.04 installation with the Update Manager.

Ampers

---

### Post by mmarif4u on 2009-06-04
Did you tried in terminal:
> sudo apt-get update

---

### Post by AmpersUK on 2009-06-04
> **mmarif4u said:**
> Did you tried in terminal:

Yes, I did try that and got:

***There was an error creating the child process for this terminal***

Ampers

---

### Post by AmpersUK on 2009-06-04
Yes, I did try that and got:

***There was an error creating the child process for this terminal***

This seems more serious than I thought. I cannot now download any programs using Add/Remove in the Applications menu or Synaptic Package Manager under System/Administration

Ampers

---

### Post by jdfilburn on 2009-10-24
Was this issue ever resolved, and if so, how?

I am facing the same challenges.

thank you for your time.

---

### Post by coffeecat on 2009-10-25
**jdfilburn**, [this is what I found with Google]("http://www.smorgasbord.net/ubuntu-update-manager-error-failed-to-fork-pt/"). I can't say whether that will work because I haven't encountered this error myself, but it seems to agree with other links that come up with the same Google search.

Hint: try googling the **exact** error message, whatever OS you are using. That's rarely failed to help me and I've googled more obscure error messages than I've had hot breakfasts. :wink: On this occasion I googled "ubuntu error failed to fork pty" and I got 10 pages of hits. Try it. There's a Launchpad bug report which might be of interest.

---

### Post by sohlside on 2009-10-25
> **AmpersUK said:**
> **Error reads:** "Error failed to fork pty"

I get the above error message when I try to update my 9.04 installation with the Update Manager.

Ampers

Try [this]("http://www.compdigitec.com/labs/2009/05/12/fixing-there-was-an-error-creating-a-child-process-for-this-terminal/").  I believe this is the solution I used when I had same error but can't be certain if mine was caused by same issue.

---

