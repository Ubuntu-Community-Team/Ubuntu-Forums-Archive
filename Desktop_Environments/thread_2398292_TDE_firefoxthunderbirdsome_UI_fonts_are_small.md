---
title: "TDE: firefox/thunderbird/some UI fonts are small"
date: 2018-08-09
forum: Desktop Environments
---

### Post by mattdawolf on 2018-08-09
I have recently returned to using TDE from KDE5. For some reason, all my gtk fonts in Thunderbird, Firefox, and a few other apps are very, very small. I've gone through every GTK theme change/config app available and upped it to 28 points, as I run 3 4K displays. Forcing a DPI change will be a global change, not just specific to firefox/thunderbird.

gtk-query-settings returns a font and size of Sans 10. Where is it pulling its information from? 

I am running Ubuntu 18.04.


```
gtk-query-settings
              gtk-double-click-time: 400
          gtk-double-click-distance: 5
                   gtk-cursor-blink: TRUE
              gtk-cursor-blink-time: 1200
           gtk-cursor-blink-timeout: 10
                   gtk-split-cursor: TRUE
                     gtk-theme-name: "Adwaita"
                gtk-icon-theme-name: "tdegtk-icon-theme"
!           gtk-fallback-icon-theme: "tdegtk-fallback-icon-theme"
                 gtk-key-theme-name: NULL
                 gtk-menu-bar-accel: "F10"
             gtk-dnd-drag-threshold: 8
                      **gtk-font-name: "Sans 10"**
!                    gtk-icon-sizes: "panel-menu-bar=24,24"
                        gtk-modules: NULL
                  gtk-xft-antialias: 1
                    gtk-xft-hinting: 1
                  gtk-xft-hintstyle: "hintslight"
                       gtk-xft-rgba: "rgb"
                        gtk-xft-dpi: 122880
              gtk-cursor-theme-name: NULL
              gtk-cursor-theme-size: 0
       gtk-alternative-button-order: FALSE
        gtk-alternative-sort-arrows: FALSE
!        gtk-show-input-method-menu: FALSE
!             gtk-show-unicode-menu: FALSE
!               gtk-timeout-initial: 500
!                gtk-timeout-repeat: 50
!                gtk-timeout-expand: 500
!                  gtk-color-scheme: ""
              gtk-enable-animations: TRUE
!              gtk-touchscreen-mode: FALSE
!               gtk-tooltip-timeout: 500
!        gtk-tooltip-browse-timeout: 60
!   gtk-tooltip-browse-mode-timeout: 500
!            gtk-keynav-cursor-only: FALSE
!            gtk-keynav-wrap-around: TRUE
                     gtk-error-bell: TRUE
!                        color-hash: ((GHashTable*) 0x562724875c60)
!          gtk-file-chooser-backend: NULL
                 gtk-print-backends: "file,cups,cloudprint"
          gtk-print-preview-command: "evince --unlink-tempfile --preview --print-settings %s %f"
               gtk-enable-mnemonics: TRUE
                  gtk-enable-accels: TRUE
!            gtk-recent-files-limit: 50
                      gtk-im-module: NULL
           gtk-recent-files-max-age: 30
           gtk-fontconfig-timestamp: 0
               gtk-sound-theme-name: "ubuntu"
   gtk-enable-input-feedback-sounds: TRUE
            gtk-enable-event-sounds: TRUE
!               gtk-enable-tooltips: TRUE
!                 gtk-toolbar-style: GTK_TOOLBAR_BOTH_HORIZ
!             gtk-toolbar-icon-size: GTK_ICON_SIZE_LARGE_TOOLBAR
!                gtk-auto-mnemonics: TRUE
    gtk-primary-button-warps-slider: TRUE
!                 gtk-visible-focus: GTK_POLICY_AUTOMATIC
  gtk-application-prefer-dark-theme: FALSE
!                 gtk-button-images: FALSE
          gtk-entry-select-on-focus: TRUE
    gtk-entry-password-hint-timeout: 0
!                   gtk-menu-images: FALSE
!          gtk-menu-bar-popup-delay: 0
!     gtk-scrolled-window-placement: GTK_CORNER_TOP_LEFT
!             gtk-can-change-accels: FALSE
!              gtk-menu-popup-delay: 225
!            gtk-menu-popdown-delay: 1000
          gtk-label-select-on-focus: TRUE
!                 gtk-color-palette: "black:white:gray50:red:purple:blue:light blue:green:yellow:orange:lavender:brown:goldenrod4:dodger blue:pink:light green:gray10:gray30:gray75:gray90"
!              gtk-im-preedit-style: GTK_IM_PREEDIT_CALLBACK
!               gtk-im-status-style: GTK_IM_STATUS_CALLBACK
           gtk-shell-shows-app-menu: FALSE
            gtk-shell-shows-menubar: FALSE
            gtk-shell-shows-desktop: TRUE
              gtk-decoration-layout: "menu:minimize,maximize,close"
          gtk-titlebar-double-click: "toggle-maximize"
          gtk-titlebar-middle-click: "none"
           gtk-titlebar-right-click: "menu"
             gtk-dialogs-use-header: FALSE
           gtk-enable-primary-paste: TRUE
           gtk-recent-files-enabled: TRUE
                gtk-long-press-time: 500
               gtk-keynav-use-caret: FALSE
```

---

### Post by QIII on 2018-08-09
Please use code tags to enclose terminal commands and their results.  Don't get carried away with special formatting to bring attention to what needs to be emphasized.  Note that a simple bold stands out.  Code tags also preserve formatting, which keeps character strings as they are, rather than having them turn into emojis.

Is is also best to say what an esoteric acronym stands for rather than to assume people will know, ie:

" ... TDE (Trinity Desktop Environment) ... "

or

" ... Trinity Desktop Environment (TDE) ... "

---

### Post by mattdawolf on 2018-08-09
Noted. Thanks.

---

