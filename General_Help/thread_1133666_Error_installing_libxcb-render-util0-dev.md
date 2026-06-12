---
title: "Error installing libxcb-render-util0-dev"
date: 2009-04-23
forum: General Help
---

### Post by rrbarbosa on 2009-04-23
Hi,

I was trying to replace my gnuplot installed from ubuntu repositories for one compiled from the source to add 'tab completion'. The problem is one of the dependencies 'libcairo2-dev' won't be installed, because it depends on 'libxcb-render-util0-dev' that won't be installed.

I understood that the 'libxcb-render-util0' version (0.2.1+git1-1) is different from the 'dev' (0.2+git36-1) I am trying to install, and that could be the source of the error.

Could somebody know how can I solve this issue? I considered removing 'libxcb-render-util0' but it seems that *many* packages that I have installed (eg. brasero, compiz, firefox) depend on it, and would also be removed, so I did not do it.

This is the error I get from apt-get
> 
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxcb-render-util0-dev: Depends: libxcb-render-util0 (= 0.2+git36-1) but 0.2.1+git1-1 is to be installed
E: Broken packages


Thanks,
Rafael

---

