---
title: "how to add new digital clock to screenlets"
date: 2009-05-24
forum: Desktop Environments
---

### Post by tonjaa on 2009-05-24
i want to know [COLOR=DarkOrange]how[/COLOR] i can [COLOR=Blue]add new digital clock to screenlets?[/COLOR]
i go to download new digital clock at my desktop .tar.bz2  how to? add it.

---

### Post by ckonestroh on 2009-05-24
I want you to understand this is usually a file built from source code and could need addition packages installed and generally is not supported to run in Ubuntu this way or is not supported by Ubuntu to be a stable program... There could be errors.....


good luck...

(Tar/GZip) archives end in ".tar.gz" and (Tar/Bzip2) archives end in ".tar.bz2". Bzip2 is the newer, more efficient compression method. These files can generally be automatically extracted by merely clicking on them from your file manager (Nautilus), since file associations with the appropriate archival utilities are set by default in Ubuntu. These instructions are for those who wish to use the command line Terminal.

        * To extract: 

tar xvf packagename.tar.gz

Note: tar is an application which can extract files from an archive, decompressing if necessary.

        -x means extract. 
        -v means verbose (list what it is extracting). 
        -f specifies the file to use. 

    * Decompressing ".gz" files 

gunzip file.gz

    * Decompressing ".bz2" files 

bunzip2 file.bz2

        Note: You can also decompress a package first by using the command gunzip (for .gz) or bunzip2 (for .bz2), leaving the .tar file. You would then use tar to extract it. 

        * To create a .gz archive: 

tar cvfz packagename.tar.gz folder

        * To create a .bz2 archive: 

tar cvfj packagename.tar.bz2 folder

[edit]
Installing a package from source

    * Make sure you have all the necessary development tools (i.e. libraries, compilers, headers): 

sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

        Note: "uname -r" lists the current kernel you are using 

    * Extract the archive that contains the source files: 

tar xvf sourcefilesarchive.tar.gz

    * Build the package using the package's script (in this case the configure script), compile the package (make), and install the compiled package into your system (make install): 

cd /path/to/extracted/sourcefiles
./configure
sudo make
sudo make install

        Note: typing ./ before a filename in the current folder allows the Linux shell to try and execute the file as an application even if it is not in the path (the set of folders which it searches when you type a command name). If you get a "permission denied" error, the file is not marked as being executable. To fix this: 

sudo chmod +x filename

        Example: In the above instructions, configure is the shell script to build the package from source. To be sure the configure script is executable: 

sudo chmod +x configure

[edit]
Create a .deb package from source files

If your build from source is successful, you can make a Debian (Ubuntu) package (.deb) for future use:

    * Install package tools: 

sudo apt-get install checkinstall

    * Rebuild package using "checkinstall": 

cd /path/to/extracted/package
./configure
sudo make
sudo checkinstall

    * Keep the resulting ".deb" file for future use. It can later be installed using: 

sudo dpkg -i packagename.deb

Note: These are basic instructions that may not always work. Some packages require additional dependencies and optional parameters to be specified in order to build them successfully. 
(Tar/GZip) archives end in ".tar.gz" and (Tar/Bzip2) archives end in ".tar.bz2". Bzip2 is the newer, more efficient compression method. These files can generally be automatically extracted by merely clicking on them from your file manager (Nautilus), since file associations with the appropriate archival utilities are set by default in Ubuntu. These instructions are for those who wish to use the command line Terminal.

        * To extract: 

tar xvf packagename.tar.gz

Note: tar is an application which can extract files from an archive, decompressing if necessary.

        -x means extract. 
        -v means verbose (list what it is extracting). 
        -f specifies the file to use. 

    * Decompressing ".gz" files 

gunzip file.gz

    * Decompressing ".bz2" files 

bunzip2 file.bz2

        Note: You can also decompress a package first by using the command gunzip (for .gz) or bunzip2 (for .bz2), leaving the .tar file. You would then use tar to extract it. 

        * To create a .gz archive: 

tar cvfz packagename.tar.gz folder

        * To create a .bz2 archive: 

tar cvfj packagename.tar.bz2 folder

[edit]
Installing a package from source

    * Make sure you have all the necessary development tools (i.e. libraries, compilers, headers): 

sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

        Note: "uname -r" lists the current kernel you are using 

    * Extract the archive that contains the source files: 

tar xvf sourcefilesarchive.tar.gz

    * Build the package using the package's script (in this case the configure script), compile the package (make), and install the compiled package into your system (make install): 

cd /path/to/extracted/sourcefiles
./configure
sudo make
sudo make install

        Note: typing ./ before a filename in the current folder allows the Linux shell to try and execute the file as an application even if it is not in the path (the set of folders which it searches when you type a command name). If you get a "permission denied" error, the file is not marked as being executable. To fix this: 

sudo chmod +x filename

        Example: In the above instructions, configure is the shell script to build the package from source. To be sure the configure script is executable: 

sudo chmod +x configure

[edit]
Create a .deb package from source files

If your build from source is successful, you can make a Debian (Ubuntu) package (.deb) for future use:

    * Install package tools: 

sudo apt-get install checkinstall

    * Rebuild package using "checkinstall": 

cd /path/to/extracted/package
./configure
sudo make
sudo checkinstall

    * Keep the resulting ".deb" file for future use. It can later be installed using: 

sudo dpkg -i packagename.deb

Note: These are basic instructions that may not always work. Some packages require additional dependencies and optional parameters to be specified in order to build them successfully.

---

### Post by tonjaa on 2009-05-24
thank you very much for make me understand more about file and command . 
i not understand about uname-r  and kernel that i using. it's name of application or name of  program ?
[COLOR=Sienna]sudo apt-get install linux-headers-`uname -r`[/COLOR] like name of my computer or not? please Exsample too.
and  can i add file to directory of application from archive not use command in terminal or ?

---

