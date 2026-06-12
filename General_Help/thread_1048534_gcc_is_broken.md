---
title: "gcc is broken"
date: 2009-01-23
forum: General Help
---

### Post by hwttdz on 2009-01-23
If I purge gcc and reinstall my gcc is broken.  I'm at a loss of what to do.  Being silly I attempted to install g77 from source, and ended up installing another version of gcc at the same time, which I then managed to screw up.  I'm happy to give any information one needs.

When synaptic thinks gcc is installed I get a "bash: gcc: command not found"

---

### Post by wirelessmonkey on 2009-01-23
Try:
```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by hwttdz on 2009-01-23
If I do
```

apt-get update
apt-get upgrade
apt-get purge gcc
apt-get install build-essential

```

I get (in addition to other info)
```

Unpacking gcc (from .../gcc_4%3a4.3.1-1ubuntu2_amd64.deb) ...
Setting up gcc (4:4.3.1-1ubuntu2) ...

```

then if I do
gcc -v:
```

The program 'gcc' can be found in the following packages:
 * gcc
 * pentium-builder
Try: sudo apt-get install <selected package>
bash: gcc: command not found

```

So it somehow thinks it's installed but it's not working all the way.

---

### Post by taurus on 2009-01-23
What if you just run

```
apt-get install build-essential
```

---

### Post by hwttdz on 2009-01-23
Removing and reinstalling build-essential had no effect.

Anyways, solved the problem using possibly the least elegant approach I've ever heard of.  
[CODE]
dpkg --get-selections|awk '{print $1}' > package_list.txt
cat package_list.txt|xargs -n 1 sudo aptitude reinstall
[\CODE]

So clearly problem could be solved reinstalling some subset of packages.  Probably less than the entire system.  But this works.  How's the saying go

If brute force doesn't work.... you're not using enough.

In a slightly different problem, I'm not seeing the mark as solved under thread tools.  Is this feature gone? (I see it's currently disabled [http://ubuntuforums.org/showthread.php?t=1046863]("http://ubuntuforums.org/showthread.php?t=1046863") ).

---

