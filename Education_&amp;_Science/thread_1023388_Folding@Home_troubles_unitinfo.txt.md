---
title: "Folding@Home troubles: unitinfo.txt"
date: 2008-12-27
forum: Education &amp; Science
---

### Post by earthmeLon on 2008-12-27
I am trying to get Folding@Home installed on my laptop.  I've installed FAH using the [fah_instal]("https://help.ubuntu.com/community/FoldingAtHome/fah_install")l install.sh script (thanks jpkotta).

I followed the installation instructions and selected the **6.02 (64 bit/SMP)** option for my x64 dual core processor.

Next, I checked htop to see if the processes were running:

```
top -b > x.txt

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
10329 foldinga  39  19  181m  95m 2652 S   52  4.7   5:46.78 FahCore_a2.exe
10330 foldinga  39  19  173m  87m 2640 S   46  4.3   5:33.31 FahCore_a2.exe
10327 foldinga  39  19  169m  80m 2924 S   37  4.0   5:28.57 FahCore_a2.exe
10328 foldinga  39  19  177m  85m 2652 S   31  4.3   5:31.50 FahCore_a2.exe
```

It's running (although I would think since I only have a 2 core processor, it would only run up to two instances of FAH, but whatever)

Next I went to /opt/foldingathome/ and noticed only one numerical directory:

```
ls /opt/foldingathome/
1  config  README  reconfigure.sh

```

That's weird. Since I have two cores, I thought I would have 1/ and 2/

But what's REALLY bothering me is that I have no unitinfo.txt in 1/

```
ls /opt/foldingathome/1/
client.cfg  FahCore_a2.exe  machinedependent.dat  MyFolding.html  state.cpt
fah6        FAHlog.txt      mpiexec               queue.dat       work

```

So, my question is: **Does anybody know what the problem might be?**  I am trying to get [Protein Think]("http://prothink.sourceforge.net/") working.  It needs this file to work v_v.
I will put some more information about my computer up hoping it will help :D

```
cat /proc/cpuinfo

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz
stepping	: 2
cpu MHz		: 800.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3458.98
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz
stepping	: 2
cpu MHz		: 800.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3459.03
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

And the end of FAHlog.txt >
```
[02:28:57] Verifying core Core_a2.fah...
[02:28:57] Signature is VALID
[02:28:57]
[02:28:57] Trying to unzip core FahCore_a2.exe
[02:28:58] Decompressed FahCore_a2.exe (4099344 bytes) successfully
[02:28:58] + Core successfully engaged
[02:29:04]
[02:29:04] + Processing work unit
[02:29:04] Core required: FahCore_a2.exe
[02:29:04] Core found.
[02:29:04] Working on Unit 01 [December 28 02:29:04]
[02:29:04] + Working ...
[02:29:04]
[02:29:04] *------------------------------*
[02:29:04] Folding@Home Gromacs SMP Core
[02:29:04] Version 2.01 (Wed Aug 13 13:11:25 PDT 2008)
[02:29:04]
[02:29:04] Preparing to commence simulation
[02:29:04] - Ensuring status. Please wait.
[02:29:06] Called DecompressByteArray: compressed_data_size=4833930 data_size=23977245, decompressed_data_size=23977245 diff=0
[02:29:06] - Digital signature verified
[02:29:06]
[02:29:06] Project: 2669 (Run 16, Clone 72, Gen 55)
[02:29:06]
[02:29:06] Assembly optimizations on if available.
[02:29:06] Entering M.D.
[02:29:17] Run 16, Clone 72, Gen 55)
[02:29:17]
[02:29:17] Entering M.D.

```

Thanks in advance for any suggestions and help :D

---

### Post by earthmeLon on 2008-12-27
**Update:**

I chmod'd /opt/foldingathome/ to 777 and restarted the daemon.  I am wondering if that was the problem, because now I have unitinfo.txt :D

Earlier the log was showing it stuck at "Entering M.D."

Not sure what the problem was, but it seems like it might be working now.


Still open for some suggestions, though :D

Edit:  It's still not working.  Work unit doesnt move past 0%

---

### Post by Zelut on 2008-12-28
I have not used the finstall.sh script, but I maintain a different F@H tool available in the Ubuntu repositories, origami.  You might give it a try and see if you have any better results.

In regards to only one directory despite having two cores that is normal.  The 64bit client will use 64bit features, but only uses the one directory.  The 32bit client will use up to eight cores however, as I understand it.

If you want to give origami a try you can use the following.  Please let me know (in #ubuntu-folding) if you have any issues:

sudo apt-get install origami ia32-libs

sudo origami install -u USERNAME -t TEAM-NUMBER -p amd64

See man origami or --help for more options.

---

### Post by oldsoundguy on 2008-12-28
Install Boinc and Boinc manager from Synaptic .. then attach the project(s) you want to work on .. I am doing Seti, Climate Prediction and Rosetta@home right now.
Using the package manager saves a lot of grief and precludes the need to use terminal.

---

### Post by earthmeLon on 2008-12-28
Thanks for the suggestion.  I am really interested in supporting Folding@Home.  I wasn't able to figure out how to get Folding@Home to run through BOINC.  Is there a way that I missed?

---

### Post by oldsoundguy on 2008-12-28
I see what you mean .. folding@home is not offered via BOINC

but they sure have a bunch of others that need computing power!
[http://boinc.berkeley.edu/projects.php](http://boinc.berkeley.edu/projects.php)

---

