---
title: "dpkg issue"
date: 2022-08-18
forum: Desktop Environments
---

### Post by nibal on 2022-08-18
Hi,

I am trying to install python-cheetah_2.4.4 to my kubuntu 20.04 PC...
```
DrWho:~/backup-> sudo dpkg -i python-cheetah_2.4.4-4_amd64.deb
[sudo] password for nikos:
(Reading database ... 244299 files and directories currently installed.)
Preparing to unpack python-cheetah_2.4.4-4_amd64.deb ...
Unpacking python-cheetah (2.4.4-4) over (2.4.4-4) ...
dpkg: dependency problems prevent configuration of python-cheetah:
python-cheetah depends on python (<< 2.8); however:
Package python is not installed.
python-cheetah depends on python (>= 2.7~); however:
Package python is not installed.
python-cheetah depends on python:any (<< 2.8); however:
python-cheetah depends on python:any (>= 2.7.5-5~); however:

dpkg: error processing package python-cheetah (--install):
dependency problems - leaving unconfigured
Processing triggers for man-db (2.9.1-1) ...
Errors were encountered while processing:
python-cheetah
```

However I already have python2.7.18 installed:
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                   Version          Architecture Description
+++-======================-================-============-================================================>
ii  python2                2.7.17-2ubuntu4  amd64        interactive high-level object-oriented language >
un  python2-doc            <none>           <none>       (no description available)
ii  python2-minimal        2.7.17-2ubuntu4  amd64        minimal subset of the Python2 language
un  python2.5-minimal      <none>           <none>       (no description available)
un  python2.6-minimal      <none>           <none>       (no description available)
ii  python2.7              2.7.18-1~20.04.3 amd64        Interactive high-level object-oriented language >
un  python2.7-argparse     <none>           <none>       (no description available)
un  python2.7-celementtree <none>           <none>       (no description available)
un  python2.7-cjkcodecs    <none>           <none>       (no description available)
un  python2.7-ctypes       <none>           <none>       (no description available)
un  python2.7-doc          <none>           <none>       (no description available)
un  python2.7-elementtree  <none>           <none>       (no description available)
ii  python2.7-minimal      2.7.18-1~20.04.3 amd64        Minimal subset of the Python language (version 2>
un  python2.7-profiler     <none>           <none>       (no description available)
un  python2.7-wsgiref      <none>           <none>       (no description available)

```

What does it need to install?

TIA
Nikos

---

### Post by SeijiSensei on 2022-08-18
> Package python is not installed.

Did you try installing just "python"?

---

### Post by ActionParsnip on 2022-08-18
[https://packages.ubuntu.com/search?keywords=python-cheetah](https://packages.ubuntu.com/search?keywords=python-cheetah)

Its in the default repos....why are you using a deb? Just run:
```

sudo apt update
sudo apt -y install python-cheetah

```

---

### Post by nibal on 2022-08-18
> **SeijiSensei said:**
> Did you try installing just "python"?

No, I didn't try installing python. Already had both python2.7.17 & python3.8.
I tried installing python and a strange package python-is-python2 installed
This time my python-cheetah installed:)

Thank you so much:)
Nikos

---

### Post by nibal on 2022-08-18
> **ActionParsnip said:**
> [https://packages.ubuntu.com/search?keywords=python-cheetah](https://packages.ubuntu.com/search?keywords=python-cheetah)

Its in the default repos....why are you using a deb? Just run:
```

sudo apt update
sudo apt -y install python-cheetah

```
Because that would install python-cheetah3.4.2...for kubumtu 20.04
I needed to downgrade to python-cheetah 2...

BR
Nikos

---

### Post by mIk3_08 on 2022-08-19
> **nibal said:**
> Because that would install python-cheetah3.4.2...for kubumtu 20.04
I needed to downgrade to python-cheetah 2...

BR
Nikos
If you need to downgrade your python I think it is better to use [COLOR=#222222][FONT=Arial]anaconda for python configuration. I don't know how you will run the python-cheetah in your system but hope you can configure it right. You know already that python is very sensitive in Linux Ubuntu Operating System. Regards and cheers.


[/FONT][/COLOR]

---

