---
title: "input in scripts"
date: 2007-06-14
forum: Desktop Environments
---

### Post by finite9 on 2007-06-14
I created my own video encoder script called videoEncoder.sh and I want to specify a file name on the same line to pass into the script.  How do I do this?

At the moment, I hard code the input video file name and derive the output file name with:

```
infile=DVcapture20070314-mini.dv
infile2=$(echo "$infile" | sed s/"\."/".\n"/g | grep "\.")
file="$infile2"mp4
```

So I just need to replace $infile with the filename i specify when running the script, like this:

```
./videoEncoder.sh myvideo.dv
```

---

### Post by gfixler on 2007-06-15
make your first line:

infile=$1

More on this [here]("http://www.ibm.com/developerworks/library/l-bash2.html"). Of course, this assumes bash, but it may work similarly in other shells. Good luck.

---

### Post by finite9 on 2007-06-15
thanks, that worked a treat.

---

