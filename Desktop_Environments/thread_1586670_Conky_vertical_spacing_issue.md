---
title: "Conky vertical spacing issue"
date: 2010-10-02
forum: Desktop Environments
---

### Post by gschoper on 2010-10-02
In my Conky config I have if_mounted statements for removable media. It appears that each if_mounted statement adds an extra line to the display if the media is not mounted. Is there a way to remedy this. See code and screenshots.

```
${font Droid Sans:style=Bold:size=9}Old Win $alignr ${fs_used /Old_Windows} / ${fs_size /Old_Windows} $alignr ${fs_used_perc /Old_Windows}%${font}
${color DE3748}${fs_bar /Old_Windows}${color}
${if_mounted /media/KINGSTON}${font Droid Sans:style=Bold:size=9}USB Stick ${alignr} ${fs_used /media/KINGSTON} / ${fs_size /media/KINGSTON} $alignr ${fs_used_perc /media/KINGSTON}%${font}
${color DE3748}${fs_bar /media/KINGSTON}${color}
${endif}
${if_mounted /media/D08B-50A5}${font Droid Sans:style=Bold:size=9}Droid ${alignr} ${fs_used /media/D08B-50A5} / ${fs_size /media/D08B-50A5} $alignr ${fs_used_perc /media/D08B-50A5}%${font}
${color DE3748}${fs_bar /media/D08B-50A5}${color}
${endif}
${color orange}${font Judas:size=9}Memory ${font}${color}${color green}${hr 2}${color}
```

Any help appreciated.

G

EDIT: Moved the end_if statements to the end of the previous line (See last screenshot):

```
${font Droid Sans:style=Bold:size=9}Old Win $alignr ${fs_used /Old_Windows} / ${fs_size /Old_Windows} $alignr ${fs_used_perc /Old_Windows}%${font}
${color DE3748}${fs_bar /Old_Windows}${color}
${if_mounted /media/KINGSTON}${font Droid Sans:style=Bold:size=9}USB Stick ${alignr} ${fs_used /media/KINGSTON} / ${fs_size /media/KINGSTON} $alignr ${fs_used_perc /media/KINGSTON}%${font}
${color DE3748}${fs_bar /media/KINGSTON}${color}${endif}
${if_mounted /media/D08B-50A5}${font Droid Sans:style=Bold:size=9}Droid ${alignr} ${fs_used /media/D08B-50A5} / ${fs_size /media/D08B-50A5} $alignr ${fs_used_perc /media/D08B-50A5}%${font}
${color DE3748}${fs_bar /media/D08B-50A5}${color}${endif}
```

---

