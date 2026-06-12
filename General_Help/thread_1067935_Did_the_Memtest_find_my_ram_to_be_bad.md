---
title: "Did the Memtest find my ram to be bad??"
date: 2009-02-12
forum: General Help
---

### Post by morbid_bean on 2009-02-12
Ok so after upgrading to 2gbs of memory, and my computer started having random problems I was told it could be the memory is bad and I should do a test.  Ran a test and heres what I got.

Now I have no idea what any of this means so please try to help me anyway you can.

Cached= 2048M
RsvdMem= 104k
MemMap= e820-Std
Cache= on
ECC= Off
Test= Std
Pass= 3
Errors= 30464
Ecc Errs= 0

And below that are a list of 10 things whith a red background.

Tst= 5
Pass= 2
Failing Address= Random letters/number for each
Good= Random letters/number for each
Bad= Random letters/number for each
Err-Bits= Random letters/number for each
Count= Random 5 digit numbers starting with 3

Also added a screenshot of what it basicly looks like but is not easy to read the text on screen:

[IMG]http://g.imagehost.org/0227/Photo-0015.jpg[/IMG]

---

### Post by jerome1232 on 2009-02-12
> **morbid_bean said:**
> Ok so after upgrading to 2gbs of memory, and my computer started having random problems I was told it could be the memory is bad and I should do a test.  Ran a test and heres what I got.

Now I have no idea what any of this means so please try to help me anyway you can.

Cached= 2048M
RsvdMem= 104k
MemMap= e820-Std
Cache= on
ECC= Off
Test= Std
Pass= 3
[COLOR="Red"]Errors= 30464[/COLOR]
Ecc Errs= 0


I'm going to vote yes it's saying your memory is causing errors. I would try removing one of the new sticks and trying again, then try with the other stick etc...

--edit-- Hey look you can see yourself in the monitor lol

---

### Post by binbash on 2009-02-12
yes you have problems with the ram, re-run the test after removing the new stick

---

### Post by kanikilu on 2009-02-12
> **jerome1232 said:**
> I'm going to vote yes it's saying your memory is causing errors. I would try removing one of the new sticks and trying again, then try with the other stick etc...

Seconded. Running the test with one module at a time is how I found I had defective RAM.

If you just bought the memory and find that one is bad, it's best to return them both and start with a new pair. Not to sound like a shill, but Crucial has a good warranty and replaced mine with no problems at all (except for an annoying long delay, but, it was over the holidays, so...).

---

### Post by morbid_bean on 2009-02-12
i actually went from 384mbs (1x256 and 1x128 stick) to a 2x 1gb...so i try one stick at a time..

---

### Post by morbid_bean on 2009-02-12
Ok heres the update... I ran one of the sticks by itself in its orriginal slot and after the walltime hit about 20 Mins it popped up the list of 10 things in red...so then i restarted with the other stick in its original slot..and after about a wall time of 35 or so mins. it showed nothing...so i assumed that ram was good...but out i was just currious and put the stick that had no errors into the other slot and after about 20 mins it pops up 2 things in red....is it possible that the ram slot is bad or something?? or was the good ram over looked better in the 2nd slot and found something.:confused:

---

### Post by kanikilu on 2009-02-12
A bad slot on the motherboard is definitely a possibility. Is there another known-good system that you can retest both modules in? Conversely, is there any known-good RAM that you can test in the suspected bad slot?

---

### Post by morbid_bean on 2009-02-12
well rite now im testing the suspected bad ram in the good slot now and see what happens then ill take my old ram and test that in the slot i may think is bad

---

### Post by Slim Odds on 2009-02-12
> **morbid_bean said:**
> well rite now im testing the suspected bad ram in the good slot now and see what happens then ill take my old ram and test that in the slot i may think is bad

Is your BIOS setup to allow for the proper timing of these chips?


I configure my BIOS to use the SPD from the chip to determine the timing. There are manual setting that might not be set right in your case.

Just an idea.

---

### Post by morbid_bean on 2009-02-12
Its only options were either Auto or Disabled I changed it disable and all it did was move the CAS# Latencey (CL) down to 2.5 instead of 3.0

---

### Post by Slim Odds on 2009-02-12
> **morbid_bean said:**
> Its only options were either Auto or Disabled I changed it disable and all it did was move the CAS# Latencey (CL) down to 2.5 instead of 3.0

That's surprising. How old is the motherboard? What type of memory? What BIOS?

Cmon, spill your guts.... :P

But honestly, those technical details might help. Of course, maybe it's just bad RAM.

---

### Post by deadlines on 2009-02-12
I'm going to agree with the other poster and say you could just have a timing/voltage issue.  If your motherboard isn't detecting the RAM properly, memtest86 can definitely report errors.  

I would try the following:

1.  Upgrade mobo to latest BIOS rev.
2.  Dig through BIOS and see if upgrading it to latest rev. allows you to set the proper specs. If so, go to step 3.  
3.  Verify the specific CAS settings and voltage for your memory are configured properly in BIOS.
4.  If you're still having problems, you might try to test them individually in a different mobo.  If you still get failures, I'd suspect one or both of the modules are bad.

---

### Post by rush_ad on 2009-05-05
> **morbid_bean said:**
> Ok so after upgrading to 2gbs of memory, and my computer started having random problems I was told it could be the memory is bad and I should do a test.  Ran a test and heres what I got.

Now I have no idea what any of this means so please try to help me anyway you can.

Cached= 2048M
RsvdMem= 104k
MemMap= e820-Std
Cache= on
ECC= Off
Test= Std
Pass= 3
Errors= 30464
Ecc Errs= 0

And below that are a list of 10 things whith a red background.

Tst= 5
Pass= 2
Failing Address= Random letters/number for each
Good= Random letters/number for each
Bad= Random letters/number for each
Err-Bits= Random letters/number for each
Count= Random 5 digit numbers starting with 3

Also added a screenshot of what it basicly looks like but is not easy to read the text on screen:

[IMG]http://g.imagehost.org/0227/Photo-0015.jpg[/IMG]

i ran memtest last night, 2-3 hours at a time, couple of times.
i got over 350 errors each time. how many errors is bad? can i still keep using my laptop? i do have random lock ups.

---

### Post by Slim Odds on 2009-05-05
> **rush_ad said:**
> i ran memtest last night, 2-3 hours at a time, couple of times.
i got over 350 errors each time. how many errors is bad? can i still keep using my laptop? i do have random lock ups.

Personally, I'd say 1 error is bad.

It only takes 1 error to lock up a system.

---

### Post by linuxvacuum on 2009-05-05
I completely agree with the previous poster... "Slim Odds". That's funny, what an appropriate nickname for this post!

The slim odds of risking using your memory with more than 0 error are more than enough to screw up important data in the long run. I made a 7zip archive while I had a bad memory stick and I ended up losing around 25% of the files included in the archive :(.

---

