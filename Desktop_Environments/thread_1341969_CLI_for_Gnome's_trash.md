---
title: "CLI for Gnome's trash?"
date: 2009-11-30
forum: Desktop Environments
---

### Post by vlc on 2009-11-30
Hi *,

does anybody know if there is a command-line interface to Gnome's trash, e.g. to put a file into the trash or to restore it via the command line?

Thanks a lot in advance!

---

### Post by whoop on 2009-11-30
Maybe just move files from and to ~/.local/share/Trash ?
That's basically what the trash functionality of a desktop environment does...

---

### Post by CyberJack on 2009-11-30
I use a small function to trash files and directories from the CLI.
Just put this function in your .bashrc or your .zshrc

Usage: trash <file's or directories>

It will create a directory with today's date so you can find your files easily.

```

function trash() {
  if [ -z "$*" ] ; then
    echo "Usage: trash <file/dir>"
  else
    DATE=$( date +%F )
    [ -d "${HOME}/.local/share/Trash/files/${DATE}" ] || mkdir -p ${HOME}/.local/share/Trash/files/${DATE}
    for FILE in $@ ; do
      mv ${FILE} ${HOME}/.local/share/Trash/files/${DATE}
      echo "${FILE} trashed!"
    done
  fi
}

```

To restore I just move the file's from the trash to a new location.
I can't remember where I found this function, so I don't know who deserves the credits.

---

### Post by vlc on 2009-11-30
Thanks for the answers!

I also found *gvfs-trash*, but this only moves a file into the trash (and updates *~/.locale/share/Trash/info*).

But I am looking for a more powerful command which also lists the trash content, restores files or clears the trash.

I think it's a pity that the original path and the deletion time are stored in *~/.locale/share/Trash/info*, but cannot be accessed easily. Or does Nautilus have a functionality I haven't found yet?

---

### Post by vlc on 2009-12-01
Found it: *sudo aptitude install trash-cli*

It ships with

[LIST]
[*]trash
[*]list-trash
[*]restore-trash
[*]empty-trash
[/LIST]

---

