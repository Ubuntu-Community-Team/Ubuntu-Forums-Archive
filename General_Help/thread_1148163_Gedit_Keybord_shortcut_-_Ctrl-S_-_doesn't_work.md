---
title: "Gedit: Keybord shortcut - Ctrl-S - doesn't work"
date: 2009-05-04
forum: General Help
---

### Post by yen on 2009-05-04
Hello, 
I work with ubuntu 10.04. There are certain shortcuts that don't work in gedit. The most needed is the ctrl+s key. By pressing this gedit does the same when pressing ctrl+i, i.e. it opens a window GoToLine.

I've already tried everything that was proposed in [this]("http://ubuntuforums.org/showthread.php?t=858437") great thread about similar problems with gedit (except for "rsynched" since I don't know how to do it). I've started this new thread because the other one is already "solved".

The problems with gedit-shortcuts in this other thread were overcome by modifying the file "accelsgedit" in the home folder ~/.gnome2/accels. But the accelsgedit file seems to be ok in my case (s. below). The relevant line has no syntax errors and looks as the same as other lines. There ist also another file in folder ~/.gnome2/accels. The name ist gedit and it has the same content as accelsgedit.

The difference to other posts with similar problems is that the problem remains when I open gedit as root (for other people posting in the quoted thread gedit worked perfectly when opened as root). Beside root there are 2 more users (a and b) on may system. The problem described here refer to one of the users (a) and to the root. I have no problems with gedit when I'm logged in as the second (b) user (which has the same rights as the a-user). So it seems to be a local user problem.

Here's the accelsgedit file:

```

; gedit GtkAccelMap rc-file         -*- scheme -*-
; this file is an automated accelerator map dump
;
; (gtk_accel_path "<Actions>/GeditWindowActions/EditRedo" "<Shift><Control>z")
; (gtk_accel_path "<Actions>/LanguagesActions/haskell" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetActionGroupToplevel/FilterMenuAction" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/SearchGoToLine" "<Control>i")
; (gtk_accel_path "<Actions>/GeditWindowActions/SearchFindNext" "<Control>g")
; (gtk_accel_path "<Actions>/FileBrowserWidgetSensitiveActionGroup/DirectoryOpen" "<Control>o")
; (gtk_accel_path "<Actions>/FileBrowserPluginSingleSelectionExtra/OpenTerminal" "")
; (gtk_accel_path "<Actions>/LanguagesActions/css" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/FileRevert" "")
; (gtk_accel_path "<Actions>/LanguagesActions/dtd" "")
; (gtk_accel_path "<Actions>/LanguagesActions/docbook" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/FilePageSetup" "")
; (gtk_accel_path "<Actions>/LanguagesActions/chdr" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/Edit" "")
; (gtk_accel_path "<Actions>/LanguagesActions/eiffel" "")
; (gtk_accel_path "<Actions>/LanguagesActions/diff" "")
; (gtk_accel_path "<Actions>/LanguagesActions/awk" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/DocumentsNextDocument" "<Control><Alt>Page_Down")
; (gtk_accel_path "<Actions>/GeditWindowActions/FileCloseAll" "<Shift><Control>w")
; (gtk_accel_path "<Actions>/LanguagesActions/sql" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/SearchFind" "<Control>f")
; (gtk_accel_path "<Actions>/LanguagesActions/scheme" "")
; (gtk_accel_path "<Actions>/GeditSpellPluginActions/ConfigSpell" "")
; (gtk_accel_path "<Actions>/LanguagesActions/libtool" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/EditCopy" "<Control>c")
; (gtk_accel_path "<Actions>/LanguagesActions/pascal" "")
; (gtk_accel_path "<Actions>/LanguagesActions/perl" "")
; (gtk_accel_path "<Actions>/LanguagesActions/vbnet" "")
; (gtk_accel_path "<Actions>/LanguagesActions/rpmspec" "")
; (gtk_accel_path "<Actions>/LanguagesActions/objc" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/EditPreferences" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/FilePrintPreview" "<Shift><Control>p")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/FileOpenURI" "<Control>l")
; (gtk_accel_path "<Actions>/LanguagesActions/nemerle" "")
; (gtk_accel_path "<Actions>/LanguagesActions/forth" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/FileSaveAll" "<Shift><Control>l")
; (gtk_accel_path "<Actions>/GeditWindowActions/ViewHighlightMode" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/SearchIncrementalSearch" "<Control>k")
; (gtk_accel_path "<Actions>/GeditQuitWindowActions/FileQuit" "<Control>q")
; (gtk_accel_path "<Actions>/GeditWindowActions/FileClose" "<Control>w")
; (gtk_accel_path "<Actions>/LanguagesActions/ruby" "")
; (gtk_accel_path "<Actions>/GeditSpellPluginActions/AutoSpell" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/Documents" "")
; (gtk_accel_path "<Actions>/LanguagesActions/latex" "")
; (gtk_accel_path "<Actions>/LanguagesActions/gtkrc" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/ViewSidePane" "F9")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/Tools" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/SearchFindPrevious" "<Shift><Control>g")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/View" "")
; (gtk_accel_path "<Actions>/LanguagesActions/m4" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/HelpAbout" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/Help" "")
; (gtk_accel_path "<Actions>/LanguagesActions/erlang" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetSensitiveActionGroup/DirectoryRefresh" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/DocumentsMoveToNewWindow" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/HelpContents" "F1")
; (gtk_accel_path "<Actions>/LanguagesActions/dpatch" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetSingleMostSelectionActionGroup/DirectoryNew" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/File" "")
; (gtk_accel_path "<Actions>/LanguagesActions/vala" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetActionGroup/FilterHidden" "")
; (gtk_accel_path "<Actions>/LanguagesActions/ocl" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetSingleSelectionActionGroup/FileRename" "")
; (gtk_accel_path "<Actions>/LanguagesActions/gettext-translation" "")
; (gtk_accel_path "<Actions>/LanguagesActions/xml" "")
; (gtk_accel_path "<Actions>/LanguagesActions/verilog" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/EditSelectAll" "<Control>a")
; (gtk_accel_path "<Actions>/LanguagesActions/objective-caml" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/FileSaveAs" "<Shift><Control>s")
; (gtk_accel_path "<Actions>/LanguagesActions/js" "")
[COLOR=Red]; (gtk_accel_path "<Actions>/GeditWindowActions/FileSave" "<Control>s")[/COLOR]
; (gtk_accel_path "<Actions>/LanguagesActions/php" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/SearchClearHighlight" "<Shift><Control>k")
; (gtk_accel_path "<Actions>/GeditSpellPluginActions/CheckSpell" "<Shift>F7")
; (gtk_accel_path "<Actions>/DocumentsListActions/Tab_1" "<Alt>2")
; (gtk_accel_path "<Actions>/DocumentsListActions/Tab_0" "<Alt>1")
; (gtk_accel_path "<Actions>/LanguagesActions/vhdl" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/EditDelete" "")
; (gtk_accel_path "<Actions>/LaunchpadIntegration/LaunchpadAppTranslate" "")
; (gtk_accel_path "<Actions>/LanguagesActions/idl" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/FileNew" "<Control>n")
; (gtk_accel_path "<Actions>/GeditWindowActions/DocumentsPreviousDocument" "<Control><Alt>Page_Up")
; (gtk_accel_path "<Actions>/GeditWindowActions/SearchReplace" "<Control>h")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/ViewStatusbar" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/EditUndo" "<Control>z")
; (gtk_accel_path "<Actions>/LanguagesActions/changelog" "")
; (gtk_accel_path "<Actions>/LanguagesActions/cpp" "")
; (gtk_accel_path "<Actions>/LaunchpadIntegration/LaunchpadAppBugs" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetActionGroup/FilterBinary" "")
; (gtk_accel_path "<Actions>/LanguagesActions/msil" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/ViewToolbar" "")
; (gtk_accel_path "<Actions>/LanguagesActions/java" "")
; (gtk_accel_path "<Actions>/LanguagesActions/octave" "")
; (gtk_accel_path "<Actions>/GeditDocInfoPluginActions/DocumentStatistics" "")
; (gtk_accel_path "<Actions>/LanguagesActions/ini" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetSelectionActionGroup/FileMoveToTrash" "")
; (gtk_accel_path "<Actions>/LanguagesActions/haskell-literate" "")
; (gtk_accel_path "<Actions>/LanguagesActions/python" "")
; (gtk_accel_path "<Actions>/LanguagesActions/lua" "")
; (gtk_accel_path "<Actions>/LanguagesActions/boo" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/ViewBottomPane" "<Control>F9")
; (gtk_accel_path "<Actions>/LaunchpadIntegration/LaunchpadAppInfo" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetSelectionActionGroup/FileDelete" "")
; (gtk_accel_path "<Actions>/LanguagesActions/r" "")
; (gtk_accel_path "<Actions>/LanguagesActions/pkgconfig" "")
; (gtk_accel_path "<Actions>/LanguagesActions/yacc" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/EditCut" "<Control>x")
; (gtk_accel_path "<Actions>/LanguagesActions/texinfo" "")
; (gtk_accel_path "<Actions>/LanguagesActions/ada" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/EditPaste" "<Control>v")
; (gtk_accel_path "<Actions>/LanguagesActions/html" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetSingleMostSelectionActionGroup/FileNew" "<Control>n")
; (gtk_accel_path "<Actions>/GeditTimePluginActions/InsertDateAndTime" "")
; (gtk_accel_path "<Actions>/LanguagesActions/d" "")
; (gtk_accel_path "<Actions>/LanguagesActions/c" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/FileOpen" "<Control>o")
; (gtk_accel_path "<Actions>/LanguagesActions/c-sharp" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/FilePrint" "<Control>p")
; (gtk_accel_path "<Actions>/LanguagesActions/sh" "")
; (gtk_accel_path "<Actions>/LanguagesActions/makefile" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/Search" "")
; (gtk_accel_path "<Actions>/LanguagesActions/tcl" "")
; (gtk_accel_path "<Actions>/LanguagesActions/gap" "")
; (gtk_accel_path "<Actions>/LanguagesActions/fortran" "")
; (gtk_accel_path "<Actions>/FileBrowserPluginExtra/SetActiveRoot" "")
; (gtk_accel_path "<Actions>/LanguagesActions/desktop" "") 
```And here's the relevant line cut from the quotation:
[COLOR=Red]; (gtk_accel_path "<Actions>/GeditWindowActions/FileSave" "<Control>s")[/COLOR]

Do you have any suggestions?

Thank you in advance, 

yen

---

