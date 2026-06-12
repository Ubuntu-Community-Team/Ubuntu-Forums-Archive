---
title: "Extraneous whitespace in [code] boxes"
date: 2011-03-26
forum: Forum Feedback &amp; Help
---

### Post by SeijiSensei on 2011-03-26
In [this posting](http://ubuntuforums.org/showpost.php?p=10603026&postcount=2) I entered a script in [noparse]```
[/noparse] tags which is displayed with a substantial amount of whitespace at the bottom of the box.  I've tried a number of things to get rid of it, but nothing seems to work.  For instance, if you look at the BBcode, you'll see I put the [noparse]
```[/noparse] tag immediately after the last line of the script without a return.  Yet vBulletin adds extraneous whitespace at the bottom of the box regardless.  It also seems like the longer the script the more whitespace it adds (compare the top and bottom scripts).

Is there a fix for this?

---

### Post by Joeb454 on 2011-03-26
It looks like it's just the CSS adding extra space to the bottom of the code sections, probably to make it easier to read, or something.

I can't say for certain whether that's the issue without looking into it in greater detail

---

### Post by mc4man on 2011-03-27
If I was to copy from any of your code boxes I only get the text, no whitespace. 

 I know one can't add a whitespace to the end of the last line, ( unless there is some trick
Ex. what I pasted in runs twice in a row, only once if copied from 
```

sudo apt-get update
sudo apt-get update 
 

```

---

### Post by CharlesA on 2011-03-27
> **Joeb454 said:**
> It looks like it's just the CSS adding extra space to the bottom of the code sections, probably to make it easier to read, or something.

I can't say for certain whether that's the issue without looking into it in greater detail
That's what it looks like to me. It's more then likely just CSS, since it doesn't mess with any of the text inside the code tags.

---

### Post by SeijiSensei on 2011-03-27
Actually I think it has to be in vBulletin's code itself.  Here's the CSS for the first of the two larger CODE boxes on the page I referenced:

```
	<pre class="alt2" dir="ltr" style="
		margin: 0px;
		padding: 6px;
		border: 1px inset;
		width: 640px;
		height: 194px;
		text-align: left;
		overflow: auto">
```

If you look at the CSS for the larger box, it's essentially identical except for a larger "height:" parameter.  So I'd guess that value is somehow calculated in vB based on the number of lines of text.  It appears that vB overestimates the amount of height required, and the degree of overestimation increases with the number of lines of text in the box.

I would have coded it differently and just used a fixed "padding-bottom" parameter for all such boxes and let the height be determined dynamically.

---

