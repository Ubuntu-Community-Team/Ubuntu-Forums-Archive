---
title: "What does this bash script error mean?"
date: 2009-04-03
forum: General Help
---

### Post by sofasurfer on 2009-04-03
In the following line from a script there is a problem...

```

read -p &#8220;Press any key&#8221;

```

When I run it I get the following result...

```

&#8220;Press
read: 51: key&#8221;: bad variable name

```

I then copies and pasted the "read..." line to my terminal and I got "bash: read: `key&#8221;': not a valid identifier"

Then I typed the same line into the terminal and it worked fine. 
So I compared the two lines. They were identicle.

EDIT::
After I posted this message I copied the "read..." line and pasted it into my terminal. Error, error, error.

Then I typed it and it worked fine.

Am I imagining this or what???

---

### Post by spibou on 2009-04-03
> **sofasurfer said:**
> In the following line from a script there is a problem...

```

read -p “Press any key”

```

Your code uses some kind of strange quotes not the normal single or double quotes within the ASCII range.

---

### Post by sofasurfer on 2009-04-03
Those are the quotes on my keyboard. They work right for everything else.

---

### Post by spibou on 2009-04-03
Copy and paste the following in your script or the command line ```
read -p 'Press any key'
```Or the following
```
read -p "Press any key"
```
Any of the above should work. Are these the same quotes in your script ?

---

### Post by sofasurfer on 2009-04-03
Yes those are the same as my quotes. And I also have tried the single quotes before.

I just tried your quotes and my script does not work. Its like the terminal command does not have any effect. I had this happen before. And after a while it started working again.

I have a feeling that I have a glitch in my system. I have never had this much trouble before. If I don't figure this out in the next few minutes I guess I will reinstall.

---

### Post by sarang on 2009-04-03
Could you please post the entire script?

---

### Post by spibou on 2009-04-03
Copy and paste the following on the command line and post the output
```
printf '%d %d' \'\' \'\"
```

---

### Post by sofasurfer on 2009-04-03
I found the problem but I do not know the cause or the solution.
spibou was correct that my quotes looked wrong.

Here is the line from my script that does not work...
```

read -p "Press any key to create an incremental backup"

```

Here is the line from the script that DOES work...
```

read -p “Press any key to create an incremental backup”

```

The possible cause may be this...
Yesterday I was using gparted and there was an option available as the program started, that had to do with altering "key maps" (I think that was the term).

I think I chose a wrong option and then stopped the program after it ran for a second or two. Then I reran the program and chose to use all the default settings. 

I bet that the second or two of running under the "alter key map" setting did the damage.

Hows that sound? Any solution?

---

### Post by sofasurfer on 2009-04-03
The output for printf '%d %d' \'\' \'\" shows nothing.

---

### Post by sarang on 2009-04-05
Hack/quickfix:

```

read -p Press\ any\ key...\ 

```

---

