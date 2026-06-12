---
title: "AMSN errors after upgrade"
date: 2006-06-11
forum: Desktop Environments
---

### Post by ironfistchamp on 2006-06-11
I upgraded my kernel from the 386 to 686 and now aMSN won't work. I ran it and it said starting amsn and then disappeared. I then removed every bit of tcl , tk and amsn and followed a guide on how to install it. Now that I have done that whenever I try to run aMSN I get this output

 Error in startup script: unknown color name "white"
    (processing "-background" option)
    invoked from within
"text $window.info -background white -width 60 -height 30 -wrap word  -yscrollcommand "$window.ys set""
    (procedure "::pluginslog::draw" line 10)
    invoked from within
"::pluginslog::draw"
    invoked from within
"if { $initialize_amsn == 1 } {
     ::pluginslog::draw
}"
    (file "pluginslog.tcl" line 205)
    invoked from within
"source pluginslog.tcl"
    ("uplevel" body line 23)
    invoked from within
"uplevel \#0 {

        source amsncore.tcl
        source ctthemes.tcl
        source progressbar.tcl  ;# Progressbar Megawidget
        source migmd5.tcl
        source des.tcl          ;# DES..."
    (procedure "reload_files" line 2)
    invoked from within
"reload_files"
    (file "/home/dstamp/msn/amsn" line 234)

If I try using the .deb from synaptic I get the error

Application initialization failed: this isn't a Tk applicationunknown color name "Black"


Can anyone help me with this?

Thanks

Ironfistchamp

---

### Post by ironfistchamp on 2006-06-11
Sorry folks. After reinstalling the NVIDIA drivers it worked. Well glad that is sorted. I am stilla  kernel n00b so don't really understand it all. I got the hang of the desktop, the command line aint so bad but the inner workings are still a mystery.

---

### Post by larsemil on 2006-06-12
i did not get it to work though.. tried with new drivers and tried removing tcl and tk... nothing got better...

---

### Post by toille on 2006-06-15
i get the same error as well. i tried installing both the one from synaptic and from the website.
using dapper and nvidia graphics with compiz installed

---

### Post by ironfistchamp on 2006-06-15
I couldnt get compiz installed :( I wish I could help but I don't really have a clue. My solution was accidental.

---

