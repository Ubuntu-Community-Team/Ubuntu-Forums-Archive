---
title: "Is Wireshark 1.0.6 available for Intrepid?"
date: 2009-03-12
forum: General Help
---

### Post by trout256 on 2009-03-12
Is Wireshark 1.0.6 available for Intrepid?

I see 1.0.3 but not 1.0.6. I see 1.0.6 only for Jaunty.

---

### Post by rybl on 2009-03-12
Not through the package manager, but you can always compile from source:

[http://media-2.cacetech.com/wireshark/src/wireshark-1.0.6.tar.bz2]("http://media-2.cacetech.com/wireshark/src/wireshark-1.0.6.tar.bz2")

---

### Post by trout256 on 2009-03-12
Cool! Now, can anyone help me with easy directions for compiling this from source?

I have never done it before.

---

### Post by b@sh_n3rd on 2009-03-29
Hi, Compiling software is nothing much, its quite interesting. To compile you need to install "build-essentials".. then run the following code.

```
# tar xjvf wireshark-1.0.6.tar.bz2
```

(use "tar xzvf" if filename ends with "*.tar.gz" instead of "*.tar.bz2") The command above extracts the archive and creates a dir with the same name as the archive, in this case, "wireshark-1.0.6". Use "ls" to check. Dir's are shown in blue. Navigate to the newly created dir and run the following,

```
# ./configure 
# make
# makeinstall
```

Thats about it. You could also check this link to have a full desc. on compiling from source. [http://www.webmonkey.com/tutorial/Compile_Software_From_Source_Code](http://www.webmonkey.com/tutorial/Compile_Software_From_Source_Code) Check this for info on installing wireshark, [http://www.wireshark.org/docs/wsug_html_chunked/ChBuildInstallBeforeBuild.html](http://www.wireshark.org/docs/wsug_html_chunked/ChBuildInstallBeforeBuild.html)
You're welcome and Good luck! :)

---

