---
title: "Setting up custom modulefiles in environment-modules on ubuntu 18.04 LTS"
date: 2019-12-26
forum: Desktop Environments
---

### Post by mdhfiz on 2019-12-26
Using `environment-modules`, I am trying to set up custom environment modules for installation of a software by using intel compiler and openmpi. I am not familiar with the method of creating a custom modulefile but I have constructed two with the aid of little resource provided on the interweb, although I can't seem to get it to work. I am using and HPC running ubuntu 18.04 LTS and this is my intel module file (../bin contains "compilervars.csh  compilervars.sh" and ../lib contains "ia32  ia32_lin  intel64  intel64_lin"):
```
    #%Module1.0#####################################################################
    ##")
    ## intel modulefile
    ##
    proc ModulesHelp { } {
        puts stderr "\tAdds Intel compilers to your environment variables,"
    
    }
    
    module-whatis "adds Intel compilers to your environment variables"
    
    setenv(  "INTELPATH",  "/opt/intel/bin")
    prepend_path( "PATH",   "/opt/intel/bin")
    prepend_path( "LD_LIBRARY_PATH", "/opt/intel/lib")

```
Next for openmpi, this is my attempt:
```
    #%Module1.0#####################################################################
    ##")
    ## openmpi modulefile
    ##
    proc ModulesHelp { } {
        puts stderr "\tAdds openmpi to your environment variables,"
    
    }
    
    module-whatis "adds openmpi to your environment variables"
    
    setenv(  "INTELPATH",  "/usr/bin")
    prepend_path( "PATH",   "/usr/bin")
    prepend_path( "LD_LIBRARY_PATH", "/usr/lib/x86_64-linux-gnu/openmpi/lib")

```This gives the following error (for intel compiler):
```
    Loading intel
       Module Error: extra characters after close-quote
       In '/usr/local/Modules/modulefiles/intel'
       Please contact <root@localhost>

```However, I'm not sure if I set this up correctly. I can't find bin folder for openmpi but found mpicc.openmpi and mpirun.openmpi in /usr/bin. I'm not sure about the lib too. Please guide me on the correct way of setting up my environment modules and fix my two modulefiles. It's quite confusing for me because I'm not familiar with this line of work as I work more on computational science. I hope I can get this to work soon. Thank you!

---

### Post by mdhfiz on 2019-12-26
I just noticed this page is not about the environment that I am referring to. I'm sorry

---

