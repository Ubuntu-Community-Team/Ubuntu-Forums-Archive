---
title: "snd_ctl_open failed. Invalid argument"
date: 2016-11-23
forum: Debian
---

### Post by carcox on 2016-11-23
I am developing an application working with sound on a board  ([https://www.olimex.com/wiki/A20-OLinuXino-LIME2](https://www.olimex.com/wiki/A20-OLinuXino-LIME2)) embedding an ARM architecture, on which a Debian distribution is present.
When I try to open the USB sound card ([https://www.amazon.com/dp/B016CU2PEU/?tag=stackoverfl08-20](https://www.amazon.com/dp/B016CU2PEU/?tag=stackoverfl08-20)) plugged to the board, I do the following:

```

    while(1){

    if((err = snd_card_next(&card_num))<0){
        cout << "Can't get next card number" << endl;
        break;
    }
    if(card_num<0) break;

    snd_ctl_t *cardHandle;
    char   str[64];
        sprintf(str, "hw:%i", card_num);

    if ((err = snd_ctl_open(&cardHandle, str, 0)) < 0){
        cout << "Can't open card " << card_num << " , error = " << snd_strerror(err) << endl;
        continue;
    }

    snd_ctl_card_info_t *cardInfo;
        // We need to get a snd_ctl_card_info_t. Just alloc it on the stack
        snd_ctl_card_info_alloca(&cardInfo);

    if ((err = snd_ctl_card_info(cardHandle, cardInfo)) < 0){
        cout << "Can't get info for card " << card_num << endl;
        continue;
    }

        const char *mixer_name = snd_ctl_card_info_get_mixername(cardInfo);


    cout << "Card num " << card_num << " , name = " << snd_ctl_card_info_get_name(cardInfo) << " , mixer = " << mixer_name << endl;
    if(strcmp(mixer_name,"") > 0) {
        current_card_selected = card_num;
    }
    snd_ctl_close(cardHandle);
}

```

But the operation fails, and I get:
"Can't open Card 0, error = Invalid Argument"
"Can't open Card 1, error = Invalid Argument" (This is the USB sound card).
My idea is that the str[64] passed is wrongly defined as "hw:0,0" or "hw:1,0" ; but I don't know which alsa configuration file to look at and change.
On my Ubuntu 16.04 Intel x86_64 laptop everything works fine.
Any hint? Thanks in advance

---

### Post by howefield on 2016-11-23
Thread moved to the "*Debian*" forum.

---

