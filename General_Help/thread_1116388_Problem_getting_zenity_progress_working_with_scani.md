---
title: "Problem getting zenity progress working with scanimage"
date: 2009-04-04
forum: General Help
---

### Post by adaniels on 2009-04-04
Hi,

I'm trying to get a progress bar for running `scanimage --batch`, using zenity. The bar stays on 0% and the text is not updated, until scanimage ends.

I use the following command.
```

scanimage --device-name avision:libusb:001:009 --format pnm --mode lineart --batch --batch-count 3 2>&1 |
awk '{if ($1=="Scanning" && $2=="page") print "# "$0; if ($1=="Scanned") print int(100*$3/3);}' |
zenity --progress --title "Scanning pages" --text="Starting" --percentage=0

```

The output of awk seems to be correct. If i just pipe this output to zenity, it works fine.
```

(
echo "# Scanning page 1";
echo "33"; sleep 1
echo "# Scanning page 2";
echo "66"; sleep 1
echo "# Scanning page 3";
echo "100"
) |   
zenity --progress --title="Scanning pages" --text="Starting" --percentage=0

```

When running the scanimage | awk command without zenity, lines are written during scanning and not all at once. Unfortunately I'm at a loss.

Does anybody know what's going wrong here?

Thanks for any help,
Arnold

---

