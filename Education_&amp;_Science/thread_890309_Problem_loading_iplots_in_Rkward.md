---
title: "Problem loading iplots in Rkward"
date: 2008-08-14
forum: Education &amp; Science
---

### Post by gvanto on 2008-08-14
I was doing some plots in R (using rkward) and then realized I needed to have some features like zooming, etc.

I have come across 'iPlots' (package: iplots) and followed all the instructions to install it...

to use iplots, I need to load the library with:
```

require(iplots) #or library(iplots)

```

Now, if I run this in (R-mode) in Konsole (running Hardy Linux), it works fine.

But when doing this in RkWard (either via the R-console within Rkward or in the package manager), I get a segmentation fault and RKward crashes!! :-((
Doing it from the R-console (in rkward) gives:
```


> require(iplots)
Loading required package: iplots
Loading required package: rJava

 *** caught illegal operation ***
address 0xb60dbde1, cause 'illegal operand'

Traceback:
 1: .External(interface, obj@jobj, returnSig, method, ..., PACKAGE = "rJava")
 2: .jcall(ic, "Ljava/lang/reflect/Field;", "getField", "TYPE")
 3: .jinit()
 4: .jpackage("iplots")
 5: f(libname, pkgname)
 6: firstlib(which.lib.loc, package)
 7: doTryCatch(return(expr), name, parentenv, handler)
 8: tryCatchOne(expr, names, parentenv, handlers[[1]])
 9: tryCatchList(expr, classes, parentenv, handlers)
10: tryCatch(expr, error = function(e) {    call <- conditionCall(e)    if (!is.null(call)) {        if (identical(call[[1]], quote(doTryCatch)))             call <- sys.call(-4)        dcall <- deparse(call)[1]        prefix <- paste("Error in", dcall, ": ")        LONG <- 75        msg <- conditionMessage(e)        sm <- strsplit(msg, "\n")[[1]]        if (14 + nchar(dcall, type = "w") + nchar(sm[1], type = "w") >             LONG)             prefix <- paste(prefix, "\n  ", sep = "")    }    else prefix <- "Error : "    msg <- paste(prefix, conditionMessage(e), "\n", sep = "")    .Internal(seterrmessage(msg[1]))    if (!silent && identical(getOption("show.error.messages"),         TRUE)) {        cat(msg, file = stderr())        .Internal(printDeferredWarnings())    }    invisible(structure(msg, class = "try-error"))})
11: try(firstlib(which.lib.loc, package))
12: library(package, lib.loc = lib.loc, character.only = TRUE, logical.return = TRUE,     warn.conflicts = warn.conflicts, keep.source = keep.source,     version = version)
13: base::require(as.character(package), quietly = quietly, character.only = TRUE,     ...)
14: require(iplots)

Possible actions:
1: abort (with core dump, if enabled)
2: normal R exit
3: exit R without saving workspace
4: exit R saving workspace


```


If anyone can provide some advice on how to overcome this problem, it would be so much appreciated!

(perhaps there's a better way to do  interactive plotting in R than with iplots?)

Gerry
iplots - newbie

---

