---
title: "Uninstalling Eclipse from Ubuntu 18.04 Command line does not work"
date: 2019-11-01
forum: Desktop Environments
---

### Post by eMshsWE on 2019-11-01
Hello,
I had installed Eclipse Java IDE software a year ago in Ubuntu 18.04. It comes under my apps as eclilpse-workspace - Eclipse IDE with this icon.

[ATTACH=CONFIG]284311[/ATTACH]
and now am trying to remove it. But it doesn't get removed when I type this in the command line
```

ramasea1 ~ $ sudo apt-get autoremove eclipse*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package eclipse-workspace

```

How should I remove this Eclipse software then? Could someone please help?
Regards,
Ajay

---

### Post by Skaperen on 2019-11-01
the subcommand you need to use instead of "autoremove" is "purge" (it also remove configuration files).  also the "*" only matches file names.  to match packages you need to put it in quotes and also use regular expression format.  try this command:
```

apt-get purge 'eclipse.*'

```

---

### Post by TheFu on 2019-11-01
autoremove isn't the option, as Skaperen says.
```
sudo apt-get remove  eclipse*

```
or
```
sudo apt-get remove --purge  eclipse*
```

There are other tools for package management, but only apt-get allows using wildcards.  The others require the exact, correct, package name(s) be used.

If you want a GUI, check out **synaptic**.

More and more, Ubuntu will be installing snap packages instead of the Debian packages which have been used since the beginning.  snaps require removal using the "snap remove" command.

As for ```
apt-get autoremove
``` ... the manpage says:
```
       autoremove (and the auto-remove alias since 1.1)
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for other packages and are now no
           longer needed.
```
It doesn't work on any specific package. It is for cleaning up other, automatically installed, dependencies. Another command which should be run at least monthly is **apt-get autoclean**:```

       autoclean (and the auto-clean alias since 1.1)
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.
```

autoclean and autoremove should both be run monthly, IMHO. This is assuming a normal Ubuntu setup with weekly patching.  Both work with apt, so we can save 4 characters. ;)

---

### Post by eMshsWE on 2019-11-06
I am not able to remove Eclipse IDE with either command. I am pasting the output of these two commands below :-

sudo apt-get remove --purge  eclipse*

```

ramasea1 ~ $ sudo apt-get remove --purge  eclipse*
[sudo] password for ramasea1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package eclipse-workspace

```

and this command 
sudo apt-get purge 'eclipse.*'
```

ramasea1 ~ $ sudo apt-get purge 'eclipse.*'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'eclipse-rse' for regex 'eclipse.*'
Note, selecting 'eclipse-xsd-sdk' for regex 'eclipse.*'
Note, selecting 'eclipse-cdt-launch-remote' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-core-di-extensions-supplier-java' for regex 'eclipse.*'
Note, selecting 'eclipse-rpm-editor' for regex 'eclipse.*'
Note, selecting 'libeclipse-ui-ide-application-java' for regex 'eclipse.*'
Note, selecting 'eclipse-mylyn-versions-cvs' for regex 'eclipse.*'
Note, selecting 'eclipse-platform-common' for regex 'eclipse.*'
Note, selecting 'libeclipse-core-resources-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-jdt-apt-pluggable-core-java' for regex 'eclipse.*'
Note, selecting 'eclipse-mylyn-tasks-github' for regex 'eclipse.*'
Note, selecting 'eclipse-cdt-qt' for regex 'eclipse.*'
Note, selecting 'eclipse-cdt-valgrind' for regex 'eclipse.*'
Note, selecting 'libeclipse-ui-monitoring-java' for regex 'eclipse.*'
Note, selecting 'golang-github-eclipse-paho.mqtt.golang-dev' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-ui-bindings-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-jdt-launching-java' for regex 'eclipse.*'
Note, selecting 'eclipse-wtp' for regex 'eclipse.*'
Note, selecting 'libeclipse-ui-console-java' for regex 'eclipse.*'
Note, selecting 'eclipse-pde-gcj' for regex 'eclipse.*'
Note, selecting 'eclipse-xsd' for regex 'eclipse.*'
Note, selecting 'libequinox-p2-touchpoint-eclipse-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-ltk-ui-refactoring-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-jdt-junit4-runtime-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-core-commands-java' for regex 'eclipse.*'
Note, selecting 'eclipse-gef-doc' for regex 'eclipse.*'
Note, selecting 'eclipse-source' for regex 'eclipse.*'
Note, selecting 'eclipse-mylyn-context-pydev' for regex 'eclipse.*'
Note, selecting 'eclipse-wtp-servertools' for regex 'eclipse.*'
Note, selecting 'libeclipse-ui-workbench-texteditor-java' for regex 'eclipse.*'
Note, selecting 'redeclipse-data' for regex 'eclipse.*'
Note, selecting 'libeclipse-ui-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-osgi-util-java' for regex 'eclipse.*'
Note, selecting 'eclipse-egit' for regex 'eclipse.*'
Note, selecting 'eclipse-wtp-ws' for regex 'eclipse.*'
Note, selecting 'libeclipse-emf-common-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-ui-model-workbench-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-core-contenttype-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-core-databinding-beans-java' for regex 'eclipse.*'
Note, selecting 'eclipse-wtp-xmltools' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-ui-dialogs-java' for regex 'eclipse.*'
Note, selecting 'eclipse-egit-mylyn' for regex 'eclipse.*'
Note, selecting 'eclipse-ptp-rdt' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-core-services-java' for regex 'eclipse.*'
Note, selecting 'eclipse-mylyn' for regex 'eclipse.*'
Note, selecting 'redeclipse-common' for regex 'eclipse.*'
Note, selecting 'libeclipse-debug-ui-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-ui-views-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-ui-workbench3-java' for regex 'eclipse.*'
Note, selecting 'eclipse-pydev-data' for regex 'eclipse.*'
Note, selecting 'eclipse-cdt-jni' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-ui-progress-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-jsch-core-java' for regex 'eclipse.*'
Note, selecting 'eclipse-mylyn-context-cdt' for regex 'eclipse.*'
Note, selecting 'eclipse-wtp-webtools' for regex 'eclipse.*'
Note, selecting 'libeclipse-team-ui-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-core-di-extensions-java' for regex 'eclipse.*'
Note, selecting 'eclipse-subclipse-graph' for regex 'eclipse.*'
Note, selecting 'eclipse-anyedit' for regex 'eclipse.*'
Note, selecting 'eclipse-jdt-gcj' for regex 'eclipse.*'
Note, selecting 'eclipse-emf-sdk' for regex 'eclipse.*'
Note, selecting 'libeclipse-osgi-compatibility-state-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-ui-workbench-renderers-swt-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-jdt-annotation-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-ui-css-swt-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-help-java' for regex 'eclipse.*'
Note, selecting 'eclipse' for regex 'eclipse.*'
Note, selecting 'libeclipse-ui-forms-java' for regex 'eclipse.*'
Note, selecting 'eclipse-remote-services-api' for regex 'eclipse.*'
Note, selecting 'libeclipse-core-expressions-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-emf-ecore-xmi-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-urischeme-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-core-variables-java' for regex 'eclipse.*'
Note, selecting 'eclipse-titan' for regex 'eclipse.*'
Note, selecting 'libeclipse-compare-java' for regex 'eclipse.*'
Note, selecting 'libequinox-p2-publisher-eclipse-java' for regex 'eclipse.*'
Note, selecting 'libcommons-jci-eclipse-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-search-java' for regex 'eclipse.*'
Note, selecting 'eclipse-subclipse-mylyn' for regex 'eclipse.*'
Note, selecting 'libeclipse-ui-browser-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-core-jobs-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-core-filesystem-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-jface-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-core-commands-java' for regex 'eclipse.*'
Note, selecting 'eclipse-mylyn-context-jdt' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-core-contexts-java' for regex 'eclipse.*'
Note, selecting 'eclipse-rse-sdk' for regex 'eclipse.*'
Note, selecting 'libeclipse-jface-text-java' for regex 'eclipse.*'
Note, selecting 'redeclipse' for regex 'eclipse.*'
Note, selecting 'libeclipse-jface-databinding-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-osgi-java' for regex 'eclipse.*'
Note, selecting 'eclipse-cdt-pkg-config' for regex 'eclipse.*'
Note, selecting 'eclipse-platform' for regex 'eclipse.*'
Note, selecting 'libeclipse-debug-core-java' for regex 'eclipse.*'
Note, selecting 'eclipse-debian-helper' for regex 'eclipse.*'
Note, selecting 'libeclipse-text-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-jdt-astview-java' for regex 'eclipse.*'
Note, selecting 'eclipse-cdt-perf' for regex 'eclipse.*'
Note, selecting 'eclipse-pydev' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-ui-workbench-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-core-externaltools-java' for regex 'eclipse.*'
Note, selecting 'eclipse-plugin-cvs' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-ui-services-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-jdt-compiler-apt-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-core-net-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-ui-genericeditor-java' for regex 'eclipse.*'
Note, selecting 'eclipse-mylyn-context-pde' for regex 'eclipse.*'
Note, selecting 'libeclipse-ui-workbench-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-ui-widgets-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-core-di-annotations-java' for regex 'eclipse.*'
Note, selecting 'libeclipselink-java-doc' for regex 'eclipse.*'
Note, selecting 'libeclipse-jdt-ui-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-ui-css-swt-theme-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-core-databinding-observable-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-core-databinding-java' for regex 'eclipse.*'
Note, selecting 'eclipse-cdt-profiling-framework' for regex 'eclipse.*'
Note, selecting 'libeclipse-team-genericeditor-diff-extension-java' for regex 'eclipse.*'
Note, selecting 'eclipse-changelog' for regex 'eclipse.*'
Note, selecting 'libeclipse-jdt-apt-core-java' for regex 'eclipse.*'
Note, selecting 'eclipse-cdt' for regex 'eclipse.*'
Note, selecting 'libeclipse-emf-ecore-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-jdt-core-java' for regex 'eclipse.*'
Note, selecting 'eclipse-subclipse' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-core-di-java' for regex 'eclipse.*'
Note, selecting 'eclipse-common-nls' for regex 'eclipse.*'
Note, selecting 'eclipse-cdt-profiling-framework-remote' for regex 'eclipse.*'
Note, selecting 'eclipse-emf' for regex 'eclipse.*'
Note, selecting 'eclipse-wtp-xsl' for regex 'eclipse.*'
Note, selecting 'eclipse-emf-examples' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-ui-di-java' for regex 'eclipse.*'
Note, selecting 'eclipse-jgit' for regex 'eclipse.*'
Note, selecting 'eclipse-cdt-autotools' for regex 'eclipse.*'
Note, selecting 'eclipse-mylyn-tasks-trac' for regex 'eclipse.*'
Note, selecting 'eclipse-gef' for regex 'eclipse.*'
Note, selecting 'eclipse-eclox' for regex 'eclipse.*'
Note, selecting 'libeclipse-ui-externaltools-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-core-filebuffers-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-ui-workbench-swt-java' for regex 'eclipse.*'
Note, selecting 'eclipse-platform-data' for regex 'eclipse.*'
Note, selecting 'libeclipse-ui-navigator-java' for regex 'eclipse.*'
Note, selecting 'eclipse-mylyn-builds-hudson' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-emf-xpath-java' for regex 'eclipse.*'
Note, selecting 'libeclipselink-java' for regex 'eclipse.*'
Note, selecting 'eclipse-platform-gcj' for regex 'eclipse.*'
Note, selecting 'redeclipse-server' for regex 'eclipse.*'
Note, selecting 'libeclipse-osgi-services-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-team-core-java' for regex 'eclipse.*'
Note, selecting 'eclipse-jdt' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-ui-workbench-addons-swt-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-ui-ide-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-jdt-debug-ui-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-jni' for regex 'eclipse.*'
Note, selecting 'libeclipse-core-runtime-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-core-databinding-property-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-ui-views-properties-tabbed-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-jdt-junit-core-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-ui-editors-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-ltk-core-refactoring-java' for regex 'eclipse.*'
Note, selecting 'eclipse-mylyn-wikitext' for regex 'eclipse.*'
Note, selecting 'libeclipse-jdt-debug-java' for regex 'eclipse.*'
Note, selecting 'eclipse-rcp-gcj' for regex 'eclipse.*'
Note, selecting 'libeclipse-jdt-core-manipulation-java' for regex 'eclipse.*'
Note, selecting 'eclipse-mylyn-tasks-bugzilla' for regex 'eclipse.*'
Note, selecting 'eclipse-pde' for regex 'eclipse.*'
Note, selecting 'eclipse-mercurialeclipse' for regex 'eclipse.*'
Note, selecting 'eclipse-platform-nls' for regex 'eclipse.*'
Note, selecting 'libeclipse-compare-core-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-jdt-compiler-tool-java' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-ui-swt-gtk-java' for regex 'eclipse.*'
Note, selecting 'golang-eclipse-paho-dev' for regex 'eclipse.*'
Note, selecting 'libeclipse-e4-ui-css-core-java' for regex 'eclipse.*'
Note, selecting 'eclipse-rcp' for regex 'eclipse.*'
Note, selecting 'libeclipse-jdt-junit-runtime-java' for regex 'eclipse.*'
Package 'eclipse-jdt-gcj' is not installed, so not removed
Package 'eclipse-pde-gcj' is not installed, so not removed
Package 'eclipse-common-nls' is not installed, so not removed
Package 'eclipse-platform-common' is not installed, so not removed
Package 'eclipse-platform-nls' is not installed, so not removed
Package 'libeclipse-jni' is not installed, so not removed
Package 'eclipse-source' is not installed, so not removed
Package 'eclipse-plugin-cvs' is not installed, so not removed
Package 'eclipse-platform-gcj' is not installed, so not removed
Package 'eclipse-rcp-gcj' is not installed, so not removed
Note, selecting 'golang-github-eclipse-paho.mqtt.golang-dev' instead of 'golang-eclipse-paho-dev'
Package 'eclipse-jgit' is not installed, so not removed
Package 'eclipse' is not installed, so not removed
Package 'eclipse-anyedit' is not installed, so not removed
Package 'eclipse-cdt' is not installed, so not removed
Package 'eclipse-cdt-autotools' is not installed, so not removed
Package 'eclipse-cdt-jni' is not installed, so not removed
Package 'eclipse-cdt-launch-remote' is not installed, so not removed
Package 'eclipse-cdt-perf' is not installed, so not removed
Package 'eclipse-cdt-pkg-config' is not installed, so not removed
Package 'eclipse-cdt-profiling-framework' is not installed, so not removed
Package 'eclipse-cdt-profiling-framework-remote' is not installed, so not removed
Package 'eclipse-cdt-qt' is not installed, so not removed
Package 'eclipse-cdt-valgrind' is not installed, so not removed
Package 'eclipse-changelog' is not installed, so not removed
Package 'eclipse-eclox' is not installed, so not removed
Package 'eclipse-egit' is not installed, so not removed
Package 'eclipse-egit-mylyn' is not installed, so not removed
Package 'eclipse-emf' is not installed, so not removed
Package 'eclipse-emf-examples' is not installed, so not removed
Package 'eclipse-emf-sdk' is not installed, so not removed
Package 'eclipse-gef' is not installed, so not removed
Package 'eclipse-gef-doc' is not installed, so not removed
Package 'eclipse-jdt' is not installed, so not removed
Package 'eclipse-mercurialeclipse' is not installed, so not removed
Package 'eclipse-mylyn' is not installed, so not removed
Package 'eclipse-mylyn-builds-hudson' is not installed, so not removed
Package 'eclipse-mylyn-context-cdt' is not installed, so not removed
Package 'eclipse-mylyn-context-jdt' is not installed, so not removed
Package 'eclipse-mylyn-context-pde' is not installed, so not removed
Package 'eclipse-mylyn-context-pydev' is not installed, so not removed
Package 'eclipse-mylyn-tasks-bugzilla' is not installed, so not removed
Package 'eclipse-mylyn-tasks-github' is not installed, so not removed
Package 'eclipse-mylyn-tasks-trac' is not installed, so not removed
Package 'eclipse-mylyn-versions-cvs' is not installed, so not removed
Package 'eclipse-mylyn-wikitext' is not installed, so not removed
Package 'eclipse-pde' is not installed, so not removed
Package 'eclipse-platform' is not installed, so not removed
Package 'eclipse-platform-data' is not installed, so not removed
Package 'eclipse-ptp-rdt' is not installed, so not removed
Package 'eclipse-pydev' is not installed, so not removed
Package 'eclipse-pydev-data' is not installed, so not removed
Package 'eclipse-rcp' is not installed, so not removed
Package 'eclipse-remote-services-api' is not installed, so not removed
Package 'eclipse-rpm-editor' is not installed, so not removed
Package 'eclipse-rse' is not installed, so not removed
Package 'eclipse-rse-sdk' is not installed, so not removed
Package 'eclipse-subclipse' is not installed, so not removed
Package 'eclipse-subclipse-graph' is not installed, so not removed
Package 'eclipse-subclipse-mylyn' is not installed, so not removed
Package 'eclipse-wtp' is not installed, so not removed
Package 'eclipse-wtp-servertools' is not installed, so not removed
Package 'eclipse-wtp-webtools' is not installed, so not removed
Package 'eclipse-wtp-ws' is not installed, so not removed
Package 'eclipse-wtp-xmltools' is not installed, so not removed
Package 'eclipse-wtp-xsl' is not installed, so not removed
Package 'eclipse-xsd' is not installed, so not removed
Package 'eclipse-xsd-sdk' is not installed, so not removed
Package 'golang-github-eclipse-paho.mqtt.golang-dev' is not installed, so not removed
Package 'libcommons-jci-eclipse-java' is not installed, so not removed
Package 'redeclipse' is not installed, so not removed
Package 'redeclipse-common' is not installed, so not removed
Package 'redeclipse-data' is not installed, so not removed
Package 'redeclipse-server' is not installed, so not removed
Package 'eclipse-debian-helper' is not installed, so not removed
Package 'eclipse-titan' is not installed, so not removed
Package 'libeclipse-compare-core-java' is not installed, so not removed
Package 'libeclipse-compare-java' is not installed, so not removed
Package 'libeclipse-core-commands-java' is not installed, so not removed
Package 'libeclipse-core-contenttype-java' is not installed, so not removed
Package 'libeclipse-core-databinding-beans-java' is not installed, so not removed
Package 'libeclipse-core-databinding-java' is not installed, so not removed
Package 'libeclipse-core-databinding-observable-java' is not installed, so not removed
Package 'libeclipse-core-databinding-property-java' is not installed, so not removed
Package 'libeclipse-core-expressions-java' is not installed, so not removed
Package 'libeclipse-core-externaltools-java' is not installed, so not removed
Package 'libeclipse-core-filebuffers-java' is not installed, so not removed
Package 'libeclipse-core-filesystem-java' is not installed, so not removed
Package 'libeclipse-core-jobs-java' is not installed, so not removed
Package 'libeclipse-core-net-java' is not installed, so not removed
Package 'libeclipse-core-resources-java' is not installed, so not removed
Package 'libeclipse-core-runtime-java' is not installed, so not removed
Package 'libeclipse-core-variables-java' is not installed, so not removed
Package 'libeclipse-debug-core-java' is not installed, so not removed
Package 'libeclipse-debug-ui-java' is not installed, so not removed
Package 'libeclipse-e4-core-commands-java' is not installed, so not removed
Package 'libeclipse-e4-core-contexts-java' is not installed, so not removed
Package 'libeclipse-e4-core-di-annotations-java' is not installed, so not removed
Package 'libeclipse-e4-core-di-extensions-java' is not installed, so not removed
Package 'libeclipse-e4-core-di-extensions-supplier-java' is not installed, so not removed
Package 'libeclipse-e4-core-di-java' is not installed, so not removed
Package 'libeclipse-e4-core-services-java' is not installed, so not removed
Package 'libeclipse-e4-emf-xpath-java' is not installed, so not removed
Package 'libeclipse-e4-ui-bindings-java' is not installed, so not removed
Package 'libeclipse-e4-ui-css-core-java' is not installed, so not removed
Package 'libeclipse-e4-ui-css-swt-java' is not installed, so not removed
Package 'libeclipse-e4-ui-css-swt-theme-java' is not installed, so not removed
Package 'libeclipse-e4-ui-di-java' is not installed, so not removed
Package 'libeclipse-e4-ui-dialogs-java' is not installed, so not removed
Package 'libeclipse-e4-ui-model-workbench-java' is not installed, so not removed
Package 'libeclipse-e4-ui-progress-java' is not installed, so not removed
Package 'libeclipse-e4-ui-services-java' is not installed, so not removed
Package 'libeclipse-e4-ui-swt-gtk-java' is not installed, so not removed
Package 'libeclipse-e4-ui-widgets-java' is not installed, so not removed
Package 'libeclipse-e4-ui-workbench-addons-swt-java' is not installed, so not removed
Package 'libeclipse-e4-ui-workbench-java' is not installed, so not removed
Package 'libeclipse-e4-ui-workbench-renderers-swt-java' is not installed, so not removed
Package 'libeclipse-e4-ui-workbench-swt-java' is not installed, so not removed
Package 'libeclipse-e4-ui-workbench3-java' is not installed, so not removed
Package 'libeclipse-emf-common-java' is not installed, so not removed
Package 'libeclipse-emf-ecore-java' is not installed, so not removed
Package 'libeclipse-emf-ecore-xmi-java' is not installed, so not removed
Package 'libeclipse-help-java' is not installed, so not removed
Package 'libeclipse-jdt-annotation-java' is not installed, so not removed
Package 'libeclipse-jdt-apt-core-java' is not installed, so not removed
Package 'libeclipse-jdt-apt-pluggable-core-java' is not installed, so not removed
Package 'libeclipse-jdt-astview-java' is not installed, so not removed
Package 'libeclipse-jdt-compiler-apt-java' is not installed, so not removed
Package 'libeclipse-jdt-compiler-tool-java' is not installed, so not removed
Package 'libeclipse-jdt-core-java' is not installed, so not removed
Package 'libeclipse-jdt-core-manipulation-java' is not installed, so not removed
Package 'libeclipse-jdt-debug-java' is not installed, so not removed
Package 'libeclipse-jdt-debug-ui-java' is not installed, so not removed
Package 'libeclipse-jdt-junit-core-java' is not installed, so not removed
Package 'libeclipse-jdt-junit-runtime-java' is not installed, so not removed
Package 'libeclipse-jdt-junit4-runtime-java' is not installed, so not removed
Package 'libeclipse-jdt-launching-java' is not installed, so not removed
Package 'libeclipse-jdt-ui-java' is not installed, so not removed
Package 'libeclipse-jface-databinding-java' is not installed, so not removed
Package 'libeclipse-jface-java' is not installed, so not removed
Package 'libeclipse-jface-text-java' is not installed, so not removed
Package 'libeclipse-jsch-core-java' is not installed, so not removed
Package 'libeclipse-ltk-core-refactoring-java' is not installed, so not removed
Package 'libeclipse-ltk-ui-refactoring-java' is not installed, so not removed
Package 'libeclipse-osgi-compatibility-state-java' is not installed, so not removed
Package 'libeclipse-osgi-java' is not installed, so not removed
Package 'libeclipse-osgi-services-java' is not installed, so not removed
Package 'libeclipse-osgi-util-java' is not installed, so not removed
Package 'libeclipse-search-java' is not installed, so not removed
Package 'libeclipse-team-core-java' is not installed, so not removed
Package 'libeclipse-team-genericeditor-diff-extension-java' is not installed, so not removed
Package 'libeclipse-team-ui-java' is not installed, so not removed
Package 'libeclipse-text-java' is not installed, so not removed
Package 'libeclipse-ui-browser-java' is not installed, so not removed
Package 'libeclipse-ui-console-java' is not installed, so not removed
Package 'libeclipse-ui-editors-java' is not installed, so not removed
Package 'libeclipse-ui-externaltools-java' is not installed, so not removed
Package 'libeclipse-ui-forms-java' is not installed, so not removed
Package 'libeclipse-ui-genericeditor-java' is not installed, so not removed
Package 'libeclipse-ui-ide-application-java' is not installed, so not removed
Package 'libeclipse-ui-ide-java' is not installed, so not removed
Package 'libeclipse-ui-java' is not installed, so not removed
Package 'libeclipse-ui-monitoring-java' is not installed, so not removed
Package 'libeclipse-ui-navigator-java' is not installed, so not removed
Package 'libeclipse-ui-views-java' is not installed, so not removed
Package 'libeclipse-ui-views-properties-tabbed-java' is not installed, so not removed
Package 'libeclipse-ui-workbench-java' is not installed, so not removed
Package 'libeclipse-ui-workbench-texteditor-java' is not installed, so not removed
Package 'libeclipse-urischeme-java' is not installed, so not removed
Package 'libeclipselink-java' is not installed, so not removed
Package 'libeclipselink-java-doc' is not installed, so not removed
Package 'libequinox-p2-publisher-eclipse-java' is not installed, so not removed
Package 'libequinox-p2-touchpoint-eclipse-java' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

After this, still Eclipse IDE runs I am unable to remove it.
Could you please help?

---

### Post by TheFu on 2019-11-06
Looks like eclipse-workspace is semi-installed still.  Reinstall that specific package - I bet there will be some failure with this that must be resolved - then try the command I provided again.

Use
```
sudo apt install  --no-install-recommends eclipse-workspace
```

On my machine, that package isn't available, so I suspect a PPA might have been used which is no longer available for some reason on your box.

---

### Post by eMshsWE on 2019-11-07
Hello,
Its still says E: Unable to locate package eclipse-workspace
I am pasting the output of the command here:

```

ramasea1 ~ $ sudo apt install  --no-install-recommends eclipse-workspace
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package eclipse-workspace

```

Does this have something to do with my cannonical package sources? Should I update them?

Regards,
Ajay

---

### Post by TheFu on 2019-11-07
**sudo apt update** needs to be run at least within a few hours BEFORE doing any other APT or package commands.  Other distros automatically update the local package cache.  Ubuntu and Debian do not.
[https://packages.ubuntu.com/search?keywords=eclipse](https://packages.ubuntu.com/search?keywords=eclipse) doesn't show eclipse-workspace package as part of the Ubuntu Universe repository, so it was either manually installed as a .deb file or using some PPA.  You'll have to figure out which.  I have no idea.

---

### Post by eMshsWE on 2019-12-18
Hello,
I ran the command sudo apt update and this is what I am getting as output
```
ramasea1 ~ $ sudo apt update
[sudo] password for ramasea1: 
Hit:1 http://in.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 https://cloud.r-project.org/bin/linux/ubuntu bionic-cran35/ InRelease    
Hit:3 http://in.archive.ubuntu.com/ubuntu bionic-updates InRelease             
Hit:4 http://in.archive.ubuntu.com/ubuntu bionic-backports InRelease           
Hit:5 http://security.ubuntu.com/ubuntu bionic-security InRelease              
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
5 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

Now I try running "sudo apt install  --no-install-recommends eclipse-workspace" but it still shows up the same error message as before
Unable to locate package
```
ramasea1 ~ $ sudo apt install  --no-install-recommends eclipse-workspace
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package eclipse-workspace
```

Could you please help me out?

---

### Post by Holger_Gehrke on 2019-12-21
Let's check a few things. If you installed Eclipse through apt, there should be a program 'eclipse' in /usr/bin/. Try:
```

which eclipse

```
This should return '/usr/bin/eclipse'. Now let's ask the lower levels of package management from what package this file was installed:
```

dpkg -S $(which eclipse)

```
On my system this returns 'eclipse-platform'. But this is **not **the main package, this is something other (language specific) packages pull in as a dependency.
Do
```

apt search eclipse|grep '\]$'

```
This should give you a list of installed packages whose name contains eclipse. The ones which have only 'installed' and not 'installed,automatic' in the brackets at the end of the line were installed manually. Those are the ones you need to remove.
Don't forget to run 'sudo apt autoremove' afterwards to get rid of all the packages that eclipse depended on and which have become (more or less) useless now that it's gone.

If 'which' returned a path beginning with '/snap/', then you didn't install eclipse through apt but as a snap package. You can find out the exact name of the package with 'snap list' and remove it with 'snap remove PACKAGE_NAME'.

If 'which' returned some other path or nothing at all, then you installed eclipse in some other way, possibly as a flatpack or from some downloaded installer bundle.

Holger

---

### Post by eMshsWE on 2019-12-21
Hi, I get no output of the command when I run "which eclipse". To make sure, that the previous command ran properly I gave echo $? and it retuned 1
```
ramasea1 ~ $ which eclipse
ramasea1 ~ $ echo $?
1

```

If echo $? returns 1, that means the previous command didn't return output. So which means the package has not been installed through apt package manager. How do I remove it then?

---

### Post by Holger_Gehrke on 2019-12-21
Not only did 'which' not give any output, a return value of '1' means 'one or more specified commands is nonexistent or not executable' according to 'man which'. If you originally installed it from the graphical 'Software' application, then it can only be either one or more deb-package(s) or a snap. So unless you remember installing it in some other way I'd try 'snap list' next. If that shows a package, than 'snap remove ' + the name of that package is the way to go. 

Otherwise you should try to find the .desktop-file that produces the icon in your apps (should be either in /usr/share/applications/ or ~/.local/share/applications/) and look at the "Exec"-line in that file (.desktop-files are just text) to find out where exactly eclipse is installed and proceed from there.

Holger

---

