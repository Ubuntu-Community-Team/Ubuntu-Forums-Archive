---
title: "requirements tu run amsn from source"
date: 2006-04-29
forum: Desktop Environments
---

### Post by eantoranz on 2006-04-29
I once in a while download amsn from the CVS so I can have a rather up2date version.

I do it at the office without problems, but I'm havig problems running it here at home... and I can't remember what packages are needed.

I'm using dapper, but I think it's not a dapper development problem, that's why I'm putting it here.

Here's the console log when I run amsn:
```

$ /usr/local/amsn/bin/amsn
Error in startup script: require dom package greater than 1.6
    while executing
"error "require dom package greater than 1.6""
    invoked from within
"if {[catch {package require dom 3.0} ::SOAP::domVersion]} {
    if { [catch {package require dom 2.0} ::SOAP::domVersion]} {
        if { [catch {pack..."
    (file "utils/tclsoap1.6.7/SOAP.tcl" line 24)
    invoked from within
"source utils/tclsoap1.6.7/SOAP.tcl"
    ("package ifneeded" script)
    invoked from within
"package require SOAP"
    invoked from within
"if { $initialize_amsn == 1 } {
        global list_BLP list_cmdhnd sb_list contactlist_loaded

        set contactlist_loaded 0

        #To be deprecated and replaced wit..."
    (file "protocol.tcl" line 4)
    invoked from within
"source protocol.tcl"
    ("uplevel" body line 20)
    invoked from within
"uplevel \#0 {

        source ctthemes.tcl
        source progressbar.tcl  ;# Progressbar Megawidget
        source migmd5.tcl
        source des.tcl          ;# DES encryption
        source s..."
    (procedure "reload_files" line 2)
    invoked from within
"reload_files"
    (file "/usr/local/amsn/bin/amsn" line 233)

```

---

