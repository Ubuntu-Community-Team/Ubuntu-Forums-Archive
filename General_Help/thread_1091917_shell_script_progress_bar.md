---
title: "shell script progress bar"
date: 2009-03-09
forum: General Help
---

### Post by civillian on 2009-03-09
I'm looking to create a shell script that will change my apt sources.list, install applications/codecs, wget and install nvidia drivers and wget themes and icons from the web, and extract them to the .themes and .icons folders.

all of this is fairly straightforwatd, however I was trying to figure out a way of getting a progress bar to display for each step (each file downloaded, copied, installed via apt-get etc).

I stumbled accross [this](http://thesweeheng.wordpress.com/2008/01/03/a-progress-bar-for-bash-scripts/) and one of my freinds cut it down to this

```
copy() { # src dst [width]
srcsize=$(stat -c %s $1) || return $?
dstsize=0
width=${3:-25}
mega=$(( 1024 * 1024 ))
start=$(date +%s)
cat $1 | (
while [[ dstsize -lt srcsize ]]
do
dd bs=512 count=2048 2>/dev/null || return $?
(( dstsize += $mega ))
[[ dstsize -gt srcsize ]] && dstsize=$srcsize

printf "\r%-20s Progress: " 1>&2

# print percentage
percent=$(( 100 * $dstsize / $srcsize ))
printf "%3d%% [" $percent 1>&2

# print progress bar
bar=$(( $width * $dstsize / $srcsize ))
for i in $(seq 1 $bar); do printf "=" 1>&2; done
for i in $(seq $bar $(( $width-1 ))); do printf " " 1>&2; done

printf "]" 1>&2
done
echo 1>&2
) | cat >$2
}
copy FILE_1 FILE_2
rm -rf FILE_2
```

eventually cutting it down even more to this:

```

copy() {
# initial values
progress=0
end=27
width=${3:-25}
while [[ progress -lt end ]]
do
printf "\r%-20s Progress: " 1>&2

# print percentage
percent=$(( 100 * $progress / $end ))
printf "%3d%% [" $percent 1>&2

# print progress bar
bar=$(( $width * $progress / $end ))
for i in $(seq 1 $bar); do printf "=" 1>&2; done
for i in $(seq $bar $(( $width-1 ))); do printf " " 1>&2; done

printf "]" 1>&2
sleep 0.1
progress=$progress+1
done
echo 1>&2
}
```

is there any way to get this to work with wget or apt-get?
if not how would I go about getting wget and apt-get to display a progress bar as part of a bash script? (ie a progress bar for each individual step, so one progress bar for apt-get install banshee, for example, and another for wget [http://www.nvidia.com/driver.run](http://www.nvidia.com/driver.run) or similar)

---

### Post by KeyserSoze93 on 2009-03-10
```
sudo apt-get install dialog
cat /usr/share/doc/dialog/examples/gauge
```

---

### Post by mal on 2009-03-10
Another option is to use zenity.  It's described in the Ubuntu help system.  It has a simple progress display dialog that can be called from a Bash script.

Mal

---

### Post by civillian on 2009-03-10
If I were to use the script that the example prints for dialog, where would I put it in my script (I'm new to shell scripting, se oxcuse n00b questions please...)?

If I wanted to use it with apt-get or wget, how would I use it?

---

