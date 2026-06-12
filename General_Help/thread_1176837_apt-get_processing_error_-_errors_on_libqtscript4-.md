---
title: "apt-get processing error - errors on libqtscript4-*/libqtscriptbindings1"
date: 2009-06-02
forum: General Help
---

### Post by victorhooi on 2009-06-02
heya,

I'm managed to get my system borked, and unable to apt-get...lol.

Basically, I was doing an apt-get update/dist-upgrade. Then, for some reason, it seemed to bork on libqtscript4-* packages.

Anyway, trying to run it again, I get a:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libqtscript4-qtbindings: Depends: libqtscript4-core (>= 0.1.0-3) but it is not installed
                           Depends: libqtscript4-gui (>= 0.1.0-3) but it is not installed
                           Depends: libqtscript4-network (>= 0.1.0-3) but it is not installed
                           Depends: libqtscript4-opengl (>= 0.1.0-3) but it is not installed
                           Depends: libqtscript4-phonon (>= 0.1.0-3) but it is not installed
                           Depends: libqtscript4-sql (>= 0.1.0-3) but it is not installed
                           Depends: libqtscript4-svg (>= 0.1.0-3) but it is not installed
                           Depends: libqtscript4-xml (>= 0.1.0-3) but it is not installed
                           Depends: libqtscript4-xmlpatterns (>= 0.1.0-3) but it is not installed
                           Depends: libqtscript4-webkit (>= 0.1.0-3) but it is not installed
                           Depends: libqtscript4-uitools (>= 0.1.0-3) but it is not installed
E: Unmet dependencies. Try using -f.

```
I then try to run 'sudo apt-get -f install, and get:
```
victorhooi@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done               
Building dependency tree                    
Reading state information... Done           
Correcting dependencies... Done             
The following packages were automatically installed and are no longer required:
  libqtscriptbindings1 virtualbox-ose-source acl                               
Use 'apt-get autoremove' to remove them.                                       
The following extra packages will be installed:                                
  libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-opengl  
  libqtscript4-phonon libqtscript4-sql libqtscript4-svg libqtscript4-uitools   
  libqtscript4-webkit libqtscript4-xml libqtscript4-xmlpatterns                
The following NEW packages will be installed:                                  
  libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-opengl  
  libqtscript4-phonon libqtscript4-sql libqtscript4-svg libqtscript4-uitools   
  libqtscript4-webkit libqtscript4-xml libqtscript4-xmlpatterns                
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.                
48 not fully installed or removed.                                             
Need to get 0B/5502kB of archives.                                             
After this operation, 20.0MB of additional disk space will be used.            
Do you want to continue [Y/n]? y                                               
(Reading database ... 169138 files and directories currently installed.)       
Unpacking libqtscript4-core (from .../libqtscript4-core_0.1.0-3_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/libqtscript4-core_0.1.0-3_amd64.deb (--unpack):                                                                                            
 trying to overwrite `/usr/lib/qt4/plugins/script/libqtscript_core.so.1.0.0', which is also in package libqtscriptbindings1                                                               
dpkg-deb: subprocess paste killed by signal (Broken pipe)                                    
Unpacking libqtscript4-gui (from .../libqtscript4-gui_0.1.0-3_amd64.deb) ...                 
dpkg: error processing /var/cache/apt/archives/libqtscript4-gui_0.1.0-3_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/qt4/plugins/script/libqtscript_gui.so.1.0.0', which is also in package libqtscriptbindings1                                                                
dpkg-deb: subprocess paste killed by signal (Broken pipe)                                    
Unpacking libqtscript4-network (from .../libqtscript4-network_0.1.0-3_amd64.deb) ...         
dpkg: error processing /var/cache/apt/archives/libqtscript4-network_0.1.0-3_amd64.deb (--unpack):                                                                                         
 trying to overwrite `/usr/lib/qt4/plugins/script/libqtscript_network.so.1.0.0', which is also in package libqtscriptbindings1                                                            
dpkg-deb: subprocess paste killed by signal (Broken pipe)                                    
Unpacking libqtscript4-opengl (from .../libqtscript4-opengl_0.1.0-3_amd64.deb) ...           
dpkg: error processing /var/cache/apt/archives/libqtscript4-opengl_0.1.0-3_amd64.deb (--unpack):                                                                                          
 trying to overwrite `/usr/lib/qt4/plugins/script/libqtscript_opengl.so.1.0.0', which is also in package libqtscriptbindings1                                                             
No apport report written because MaxReports is reached already                               
                                                              Unpacking libqtscript4-phonon (from .../libqtscript4-phonon_0.1.0-3_amd64.deb) ...                                          
dpkg: error processing /var/cache/apt/archives/libqtscript4-phonon_0.1.0-3_amd64.deb (--unpack):                                                                                          
 trying to overwrite `/usr/lib/qt4/plugins/script/libqtscript_phonon.so.1.0.0', which is also in package libqtscriptbindings1                                                             
No apport report written because MaxReports is reached already                               
                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)                                                                   
Unpacking libqtscript4-sql (from .../libqtscript4-sql_0.1.0-3_amd64.deb) ...                 
dpkg: error processing /var/cache/apt/archives/libqtscript4-sql_0.1.0-3_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/qt4/plugins/script/libqtscript_sql.so.1.0.0', which is also in package libqtscriptbindings1                                                                
No apport report written because MaxReports is reached already                               
                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)                                                                   
Unpacking libqtscript4-svg (from .../libqtscript4-svg_0.1.0-3_amd64.deb) ...                 
dpkg: error processing /var/cache/apt/archives/libqtscript4-svg_0.1.0-3_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/qt4/plugins/script/libqtscript_svg.so.1.0.0', which is also in package libqtscriptbindings1                                                                
No apport report written because MaxReports is reached already                               
                                                              Unpacking libqtscript4-xml (from .../libqtscript4-xml_0.1.0-3_amd64.deb) ...                                                
dpkg: error processing /var/cache/apt/archives/libqtscript4-xml_0.1.0-3_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/qt4/plugins/script/libqtscript_xml.so.1.0.0', which is also in package libqtscriptbindings1                                                                
No apport report written because MaxReports is reached already                               
                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)                                                                   
Unpacking libqtscript4-xmlpatterns (from .../libqtscript4-xmlpatterns_0.1.0-3_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/libqtscript4-xmlpatterns_0.1.0-3_amd64.deb (--unpack):                                                                                     
 trying to overwrite `/usr/lib/qt4/plugins/script/libqtscript_xmlpatterns.so.1.0.0', which is also in package libqtscriptbindings1                                                        
No apport report written because MaxReports is reached already                               
                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)                                                                   
Unpacking libqtscript4-webkit (from .../libqtscript4-webkit_0.1.0-3_amd64.deb) ...           
dpkg: error processing /var/cache/apt/archives/libqtscript4-webkit_0.1.0-3_amd64.deb (--unpack):                                                                                          
 trying to overwrite `/usr/lib/qt4/plugins/script/libqtscript_webkit.so.1.0.0', which is also in package libqtscriptbindings1                                                             
No apport report written because MaxReports is reached already                               
                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libqtscript4-uitools (from .../libqtscript4-uitools_0.1.0-3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libqtscript4-uitools_0.1.0-3_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/qt4/plugins/script/libqtscript_uitools.so.1.0.0', which is also in package libqtscriptbindings1
No apport report written because MaxReports is reached already
                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libqtscript4-core_0.1.0-3_amd64.deb
 /var/cache/apt/archives/libqtscript4-gui_0.1.0-3_amd64.deb
 /var/cache/apt/archives/libqtscript4-network_0.1.0-3_amd64.deb
 /var/cache/apt/archives/libqtscript4-opengl_0.1.0-3_amd64.deb
 /var/cache/apt/archives/libqtscript4-phonon_0.1.0-3_amd64.deb
 /var/cache/apt/archives/libqtscript4-sql_0.1.0-3_amd64.deb
 /var/cache/apt/archives/libqtscript4-svg_0.1.0-3_amd64.deb
 /var/cache/apt/archives/libqtscript4-xml_0.1.0-3_amd64.deb
 /var/cache/apt/archives/libqtscript4-xmlpatterns_0.1.0-3_amd64.deb
 /var/cache/apt/archives/libqtscript4-webkit_0.1.0-3_amd64.deb
 /var/cache/apt/archives/libqtscript4-uitools_0.1.0-3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Is there something I can do to break out of this loop and fix this?

Thanks,
Victor

---

### Post by jjmatt on 2009-07-19
Hey, has anyone found a solution to this?

---

### Post by Achilles124 on 2009-07-19
Don't know it, but I have found this:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/269096]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/269096")

---

### Post by jjmatt on 2009-07-19
Hmmm, alright, I decided to just manually uninstall the offending packages with dpkg. I tried:

```
$ sudo dpkg -P libqt4-core 
dpkg: dependency problems prevent removal of libqt4-core:
 skype depends on libqt4-core (>= 4.2.1); however:
  Package libqt4-core is to be removed.
```

So I removed skype

```
$ sudo dpkg -r skype
```

then ran 

```
$ sudo apt-get install -f
```

And everything went fine.

---

### Post by tehk on 2009-08-13
i had the same problem right after i lept over the "bleeding edge cliff" and upgraded to karmic koala.

i had to use dpkg to remove amarok and then the libqtscript4-qtbindings package...

after that, everything went smooth!

---

### Post by jedix on 2009-12-09
I also hit this issue when upgrading from 9.04 to 9.10.  I had to run

<code>
dpkg -r libqtscriptbindings1
apt-get -f install
apt-get dist-upgrade
</code>

This will remove the offending package, fix the install, and continue the upgrade that failed.

---

### Post by jedix on 2009-12-09
I also hit this issue when upgrading from 9.04 to 9.10.  I had to run

```

dpkg -r libqtscriptbindings1
apt-get -f install
apt-get dist-upgrade

```

This will remove the offending package, fix the install, and continue the upgrade that failed.

---

