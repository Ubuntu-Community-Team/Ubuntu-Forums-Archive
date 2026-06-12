---
title: "emerald and compizfusion problem... (n00b)"
date: 2008-02-27
forum: Desktop Effects &amp; Customization
---

### Post by WagsMKIV on 2008-02-27
I just upgraded my computer to ubuntu 7.10 and installed CompizFusion - I am hoping that this is just a n00b error or but I cannot access/find the Emerald Theme Manager. I have enabled the "windows decorations" plug-in under the CCSM but see nothing that even mentions emerald. On the CompizFusion wiki it states that *"The Emerald Theme Manager allows you to install, edit and switch between Emerald themes. In order for it to work, select Emerald as your window decorator."*. How do you select Emerald as your window decorator?

---

### Post by ajeetraj on 2008-02-27
I am hoping that you have installed emerald and emerald-theme-manager. if you haven't then try this in your terminal:

```
sudo apt-get install emerald emerald-theme-manager
```

Just remember to have all the required repos on. 

Then to switch between emerald theme and the metacity do this in the terminal:
To use emerald theme: 
```
emerald --replace
```
To come back to metacity:
```
metacity --replace
```

Hope this helps!

---

### Post by WagsMKIV on 2008-02-27
Thanks pal! I had tried this code in the terminal once before but it said that the packages could not be found. My problem was that I had changed my repository's but never reloaded them x_x . after I reloaded them I could pull up emerald in Synaptic. Thanks again!

---

### Post by fermada on 2008-03-01
I just installed Ubuntu last night so I know almost nothing about Linux. I tried to install emerald by typing:
 **sudo apt-get install emerald emerald-theme-manager**

And I got the message:** E: Couldn't find package emerald-theme-manager**
I'm not sure where to go from here.

---

### Post by sixtysixwatts on 2008-03-01
Please run sudo update first

---

### Post by rainwalker on 2008-03-01
You only need to install "emerald", there's no "emerald-theme-manager" package that I know of

---

### Post by doondoon on 2008-03-03
n00b,
I feel your pain. I had the same results you did. I think its funny however some of the responses you have received. What I have discovered is there is an emerald-theme-manager, you can find out more about it [here]("www.beryl-project.org"). The other thing I found is typing "sudo update" returns:~$ sudo update
sudo: update: command not found. 

You can install emerald however, I did it this morning and this is what I got:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libemeraldengine0
Recommended packages:
  emerald-themes
The following NEW packages will be installed:
  emerald libemeraldengine0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 299kB of archives.
After unpacking 1348kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe libemeraldengine0 0.3~git20070717-0ubuntu1 [91.1kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe emerald 0.3~git20070717-0ubuntu1 [208kB]
Fetched 299kB in 1s (236kB/s)
Selecting previously deselected package libemeraldengine0.
(Reading database ... 122365 files and directories currently installed.)
Unpacking libemeraldengine0 (from .../libemeraldengine0_0.3~git20070717-0ubuntu1_amd64.deb) ...
Selecting previously deselected package emerald.
Unpacking emerald (from .../emerald_0.3~git20070717-0ubuntu1_amd64.deb) ...
Setting up libemeraldengine0 (0.3~git20070717-0ubuntu1) ...

Setting up emerald (0.3~git20070717-0ubuntu1) ...
Unknown media type in type 'chemical/x-alchemy'

Unknown media type in type 'chemical/x-cache'

Unknown media type in type 'chemical/x-cactvs-ascii'

Unknown media type in type 'chemical/x-cactvs-binary'

Unknown media type in type 'chemical/x-cactvs-table'

Unknown media type in type 'chemical/x-cdx'

Unknown media type in type 'chemical/x-cdxml'

Unknown media type in type 'chemical/x-chem3d'

Unknown media type in type 'chemical/x-cif'

Unknown media type in type 'chemical/x-cml'

Unknown media type in type 'chemical/x-daylight-smiles'

Unknown media type in type 'chemical/x-dmol'

Unknown media type in type 'chemical/x-gamess-input'

Unknown media type in type 'chemical/x-gamess-output'

Unknown media type in type 'chemical/x-gaussian-input'

Unknown media type in type 'chemical/x-gaussian-log'

Unknown media type in type 'chemical/x-genbank'

Unknown media type in type 'chemical/x-gulp'

Unknown media type in type 'chemical/x-hin'

Unknown media type in type 'chemical/x-inchi'

Unknown media type in type 'chemical/x-inchi-xml'

Unknown media type in type 'chemical/x-jcamp-dx'

Unknown media type in type 'chemical/x-macromodel-input'

Unknown media type in type 'chemical/x-mdl-molfile'

Unknown media type in type 'chemical/x-mdl-rdfile'

Unknown media type in type 'chemical/x-mdl-rxnfile'

Unknown media type in type 'chemical/x-mdl-sdfile'

Unknown media type in type 'chemical/x-mdl-tgf'

Unknown media type in type 'chemical/x-mmcif'

Unknown media type in type 'chemical/x-mol2'

Unknown media type in type 'chemical/x-mopac-graph'

Unknown media type in type 'chemical/x-mopac-input'

Unknown media type in type 'chemical/x-mopac-out'

Unknown media type in type 'chemical/x-msi-car'

Unknown media type in type 'chemical/x-msi-hessian'

Unknown media type in type 'chemical/x-msi-mdf'

Unknown media type in type 'chemical/x-msi-msi'

Unknown media type in type 'chemical/x-ncbi-asn1'

Unknown media type in type 'chemical/x-ncbi-asn1-binary'

Unknown media type in type 'chemical/x-ncbi-asn1-xml'

Unknown media type in type 'chemical/x-pdb'

Unknown media type in type 'chemical/x-shelx'

Unknown media type in type 'chemical/x-vmd'

Unknown media type in type 'chemical/x-xyz'


Processing triggers for libc6 ...
ldconfig deferred processing now taking place
bill@bill-desktop:~$ emerald
emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"
So just like you I am not much further along than when I started. I'm hoping someone who has actually got the emerald-theme-manager running on their machine will respond.
Maybe someone from Compiz or Ubuntu[RIGHT]](*,)[/RIGHT][www.beryl-project.org]("www.beryl-project.org")

This just in: if you have apt-get installed emerald now just open the shell and type emerald-theme-manager and the "emerald-themer" will open and you can go from there.
Once you open it select themes and then you may want to select repositories and it shouldn't be hard to figure out from there. I mean I did.

---

