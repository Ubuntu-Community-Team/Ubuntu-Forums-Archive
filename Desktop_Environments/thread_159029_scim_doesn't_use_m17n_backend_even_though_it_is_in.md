---
title: "scim doesn't use m17n backend even though it is installed"
date: 2006-04-12
forum: Desktop Environments
---

### Post by eudoxos on 2006-04-12
Hello everybody,

I would like to ask if there are some special steps needed to tell scim it should use m17n as backend (scim-m17n package). scim-setup doesn't show m17n under IMengines, neither do its modules appear under the general settings.

I tried installing scim-uim and uim modules could be used immediately. But m17n is stubbornly ignored by scim.

I have ~/.xsession.d/30im-scim created by set-m17n-env, which contains
```
unset XMODIFIERS
unset GTK_IM_MODULE
scim -d
GDK_USE_XFT=1; export GDK_USE_XFT
GTK_IM_MODULE="scim" ; export GTK_IM_MODULE
XMODIFIERS="@im=SCIM" ; export XMODIFIERS
```
and ~/.scim/global
```
/DefaultConfigModule = socket
/DefaultKeyboardLayout = Czech
/DefaultPanelProgram = scim-panel-gtk
/DisabledIMEngineFactories = c6bebc27-6324-4b77-8ad4-6d41dcaf2e08
/SupportedUnicodeLocales = en_US.UTF-8,cs_CZ.UTF-8
```
(huh, not sure what /DisabledImEngineFactories means). Locales are set to is cs_CZ.UTF-8.

Any ideas? If you need additional info, I will hapily provide it.

Thanks,

Eudoxos

---

