---
title: "IPA keyboard"
date: 2006-06-17
forum: Desktop Environments
---

### Post by precinto on 2006-06-17
I can't seem to find a way to set a International Phonetic Alphabet keymap. I thought I could set a keyboard distribution through the keyboard preferences, but it isn't there. 

I haven't been able to find any info on this in the forum or Google.
Does someone know of an easy way to get the IPA keymap installed without creating one from scratch?

Thanks.

---

### Post by vladozan on 2006-06-21
[QUOTE=precinto]I can't seem to find a way to set a International Phonetic Alphabet keymap. I thought I could set a keyboard distribution through the keyboard preferences, but it isn't there. 

I haven't been able to find any info on this in the forum or Google.
Does someone know of an easy way to get the IPA keymap installed without creating one from scratch?

Thanks.[/QUOTE]

I have downloaded IPA sans fonts from the official page of IPA and unpaced them into /usr/share/fonts/truetype directory. i can run them only in text editor but at least i can. Does anyone know how to make these fonts work with abiword or open office?

---

### Post by sup on 2006-10-16
eh, I just installed them (I got the files from my teacher, or they can be downloaded from [here]("http://fu.ff.cuni.cz/vyuka/transaj/")), chmod the mto 744 (although that should not be neccesary) and a file that uses them worked strightforwardly, so I do not know what is the problem. I just have to figure out how to write them but it should be easy, I hope...

---

### Post by sup on 2006-10-16
huh, it is not, gedit handles it but openoffice does not, when it comes to writing:-/

---

### Post by sup on 2006-10-17
so abiword works well with IPA fonts, but I just have not fugured yet what keys are assignet to what signs, is there a table or something somewhere?

---

### Post by The Headhunter on 2006-10-30
I see there are fellow linguists here :-).  What you have to do first is install "scim", which is a package that can be found when you go to the Synaptic Package Manager under System -> Administration.  Also, you want to install "scim-tables-additional".  You will want to take a look at this link [https://help.ubuntu.com/community/SCIM]("https://help.ubuntu.com/community/SCIM"), specifically, the portion entitled "Additional configuration if you're not using a CJK session".  Now, what should happen is that you should see something in the panel at the top next to where the clock would be, that looks something like a keyboard.  **RIGHT**-click on it and go to SCIM setup.  Go to "Global Setup" under "IMEngine" and you see something that says "The installed input method services".  You'll see a bunch of cool input services like Amharic, Japanese, Russian, among other languages, but at the very bottom, you'll see a category "Other".  When you click the arrow on that, you'll see IPA-X-SAMPA with a little schwa icon next to it.  That's what you want.  Click the checkbox and it should install it.  Then, when you want to access it from now on (which by the way, you can in any program that allows text input), you can **LEFT**-click on it and you'll find that input method under "Other".  Now, you'll have to figure out exactly which keys on the keyboard correspond to which phonetic symbol, but a lot of that is logical.  For example, /e/ is just simply lower-case e while /&#603;/ you can get by pressing the shift-key and e, as if you were going to do a capital e, and sometimes, one key has multiple phonetic symbols that you have to choose from using the arrow keys.  I hope this helps.

---

### Post by sup on 2006-11-01
Well, thanks, but the bit about reverting the changes only with reinstalling ubuntu is scarying me a little... and my main problem with figuring what symbol corresponds to which key still remains unsolved - I am fine with using abiword with IPA and there it works with fonts given to me by my teacher out of the box.

but thanks anyway

---

### Post by sup on 2006-11-01
[here]("http://www.openoffice.org/issues/show_bug.cgi?id=71086") is why it will not work with openoffice - at least if you do nto have unicode fonts

---

### Post by sup on 2007-05-17
it finally works with OO 2.2.

---

