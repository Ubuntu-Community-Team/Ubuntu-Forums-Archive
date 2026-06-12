---
title: "Master volume with digital speakers?"
date: 2006-06-26
forum: Desktop Environments
---

### Post by justDIY on 2006-06-26
Hello Everyone!

Nice forums you've got here ... a lot of problems solved with some searching.

One problem I haven't found many results on, perhaps for lack of good keywords, is how to setup a "master" volume for all apps... oh and the catch, I'm using the sp/dif digital output on my nforce2 board.

I've edited my .asoundrc and /etc/modules to have the sp/dif output work as 'default', but none of the mixer applications (i've tried them all) can control the volume.  for something like xmms, its not a problem, since it has built in volume control... but for apps like gaim and just gnome's various sounds, they're really LOUD.  my speakers don't have an easy to access volume control, so I just leave it cranked up and adjust in software.

all suggestions are appericated!

thanks,

justDIY

---

### Post by ingomueller.net on 2007-01-11
Hi!

I had a similar problem one month ago and have spent a lot of time in its solution. As I stumbled upon this post, probably others will, so I'll post the link to a howto I wrote:

[http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume](http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume)

I hope this helps someone...

Ingo

---

### Post by luke16 on 2007-02-24
> **ingomueller.net said:**
> Hi!

I had a similar problem one month ago and have spent a lot of time in its solution. As I stumbled upon this post, probably others will, so I'll post the link to a howto I wrote:

[http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume](http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume)

I hope this helps someone...

Ingo

Thanks for the guide.

But I am a bit confused as to exactly what my device name is. The
speaker-test command works when with the device as default, but not
whenever I try putting in the device name manually.
The aplay command gives me the following, and I would assume that
the device name is cards.pcm.iec958, but that doesn't work with speaker-
test.

luke@spock:~$ aplay -L
PCM list:
hw **
        @args.0 CARD
        @args.1 DEV
        @args.2 SUBDEV
        @args.CARD **
                type string
                default **
                        @func getenv
                        vars **
                                0 ALSA_PCM_CARD
                                1 ALSA_CARD
                        }
                        default **
                                @func refer
                                name 'defaults.pcm.card'
                        }
                }
        }
        @args.DEV **
                type integer
                default **
                        @func igetenv
                        vars **
                                0 ALSA_PCM_DEVICE
                        }
                        default **
                                @func refer
                                name 'defaults.pcm.device'
                        }
                }
        }
        @args.SUBDEV **
                type integer
                default **
                        @func refer
                        name 'defaults.pcm.subdevice'
                }
        }
        type hw
        card $CARD
        device $DEV
        subdevice $SUBDEV
}
plughw **
        @args.0 CARD
        @args.1 DEV
        @args.2 SUBDEV
        @args.CARD **
                type string
                default **
                        @func getenv
                        vars **
                                0 ALSA_PCM_CARD
                                1 ALSA_CARD
                        }
                        default **
                                @func refer
                                name 'defaults.pcm.card'
                        }
                }
        }
        @args.DEV **
                type integer
                default **
                        @func igetenv
                        vars **
                                0 ALSA_PCM_DEVICE
                        }
                        default **
                                @func refer
                                name 'defaults.pcm.device'
                        }
                }
        }
        @args.SUBDEV **
                type integer
                default **
                        @func refer
                        name 'defaults.pcm.subdevice'
                }
        }
        type plug
        slave.pcm **
                type hw
                card $CARD
                device $DEV
                subdevice $SUBDEV
        }
}
plug **
        @args.0 SLAVE
        @args.SLAVE **
                type string
        }
        type plug
        slave.pcm $SLAVE
}
shm **
        @args.0 SOCKET
        @args.1 PCM
        @args.SOCKET **
                type string
        }
        @args.PCM **
                type string
        }
        type shm
        server $SOCKET
        pcm $PCM
}
tee **
        @args.0 SLAVE
        @args.1 FILE
        @args.2 FORMAT
        @args.SLAVE **
                type string
        }
        @args.FILE **
                type string
        }
        @args.FORMAT **
                type string
                default raw
        }
        type file
        slave.pcm $SLAVE
        file $FILE
        format $FORMAT
}
file **
        @args.0 FILE
        @args.1 FORMAT
        @args.FILE **
                type string
        }
        @args.FORMAT **
                type string
                default raw
        }
        type file
        slave.pcm null
        file $FILE
        format $FORMAT
}
null **
        type null
}
cards 'cards.pcm'
front 'cards.pcm.front'
rear 'cards.pcm.rear'
center_lfe 'cards.pcm.center_lfe'
side 'cards.pcm.side'
surround40 'cards.pcm.surround40'
surround41 'cards.pcm.surround41'
surround50 'cards.pcm.surround50'
surround51 'cards.pcm.surround51'
surround71 'cards.pcm.surround71'
iec958 'cards.pcm.iec958'
spdif 'cards.pcm.iec958'
modem 'cards.pcm.modem'
phoneline 'cards.pcm.phoneline'
default 'cards.pcm.default'
dmix 'cards.pcm.dmix'
dsnoop 'cards.pcm.dsnoop'

---

