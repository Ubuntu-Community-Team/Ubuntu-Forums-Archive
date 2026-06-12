---
title: "[ALSA] hda-codec - Re-add quirk support for Dell XPS 1330"
date: 2008-01-25
forum: Dell  Ubuntu Support
---

### Post by ontwerp on 2008-01-25
New kernel 2.6.24! 

About new kernel : sourcehttp://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.24

m1330 :

commit a3a2f429e55997e3b7a0c23baf1208991970ecc1
Author: Takashi Iwai <tiwai@suse.de>
Date:   Thu Oct 11 11:21:21 2007 +0200

    [ALSA] hda-codec - Fix input_mux numbers for vaio stac92xx
    
    My bad, I forgot to update the num_items field when added a new item
    to vaio_mux items table, so the last item 'PCM' disappeared.
    Now it has the right number 3.
    
    Signed-off-by: Takashi Iwai <tiwai@suse.de>
    Signed-off-by: Jaroslav Kysela <perex@suse.cz>

commit 5e915bb3677f1369223a87e488c340236f81bfc2
Author: Tim Gardner <tim.gardner@canonical.com>
Date:   Wed Oct 10 10:42:00 2007 +0200

    [ALSA] hda-codec - Re-add quirk support for Dell XPS 1330 and Inspiron 1420
    
    
    Signed-off-by: Tim Gardner <tim.gardner@canonical.com>
    Signed-off-by: Takashi Iwai <tiwai@suse.de>
    Signed-off-by: Jaroslav Kysela <perex@suse.cz>

:guitar:

---

### Post by drsaamah on 2008-01-26
i hate to sound stupid... but what exactly on the 1330 does this fix?

---

### Post by LiquidIQ on 2008-01-26
Enables the digital mic support on the M1330 and 1420.

---

### Post by bimargulies on 2008-01-26
How does one get this onto Gutsy Gibbon?

---

