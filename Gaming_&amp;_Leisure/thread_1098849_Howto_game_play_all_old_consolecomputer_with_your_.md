---
title: "Howto game play all old console/computer with your multimedia freevo center. Enjoy!"
date: 2009-03-17
forum: Gaming &amp; Leisure
---

### Post by patrick295767 on 2009-03-17
Hi,

This should be added to your /home/freevo/.freevo/local_conf.py

```



GAMES_ITEMS = [ 

('Super Nintendo 32 SNES', '/home/freevo/roms/zsnes',
        ('SNES', '/usr/bin/zsnes', '-r 2', '', None )) , 


('NEOGEO Console', '/home/freevo/roms/neogeo',
        ('SNES', 'gngeo', '-f ', '',  [ 'zip' ] )) ,



('Nesemu', '/home/freevo/roms/nes',
               ('GENERIC', 'freevomednafen','', '', ['nes' , 'zip' ])) ,

 ('Arcade Mame games cafe', '/home/freevo/roms/mame',
                ('GENERIC', 'sdlmame', ' ', '', [ 'zip' ] )),


 ('Sega Genesis', '/home/freevo/roms/genesis',('GENERIC', '/usr/bin/dgen', '-j -f -G 800x600', '', [ 'bin','zip' , 'sms' ] )), 

 ('Sega CD 16b', '/home/freevo/roms/segacd',
                ('GENERIC', 'gensfullscreen', ' ', '', [ 'iso', 'ISO' ] )),

 ('Sega CD 32X', '/home/freevo/roms/sega32x',
                ('GENERIC', 'gensfullscreen', ' ', '', [ 'bin' ] )),


 ('Sony playstation 1', '/home/freevo/roms/psx',('GENERIC', 'pcsx', ' ', '', [ 'bin','zip', 'iso', 'rar', '7z' ] )), 

	('Super Nintendo 64', '/home/freevo/roms/snes64',('SNES', '/usr/bin/zsnes', '-1 6 -2 6 -m -r 3 -k 100 -cs -t', '', None )),


 ('turbografx16', '/home/freevo/roms/pcfx',
                ('GENERIC', 'freevomednafen', ' ', '', [ 'pce', 'zip' ] )),


 ('turbografx16-CD', '/home/freevo/roms/tbfx16cd',
                ('GENERIC', 'freevomednafen', ' ', '', [ 'cue' ] )),

 ('game boy classic', '/home/freevo/roms/gbc',
                ('GENERIC', 'freevomednafen', ' ', '', [ 'gbc', 'gb', 'zip' ] )),


 ('game boy advanced', '/home/freevo/roms/gba',
                ('GENERIC', 'freevomednafen', ' ', '', [ 'gba', 'zip' ] )),

 ('Atari ST STE STF', '/home/freevo/roms/atarist',
                ('GENERIC', 'hatari', ' ', '', [ 'st', 'msa', 'zip' ] )),

 ('atari lynx', '/home/freevo/roms/lynx',
                ('GENERIC', 'freevomednafen', ' ', '', [ 'lnx', 'zip' ] )),


 ('neo geo pocket', '/home/freevo/roms/ngp',
                ('GENERIC', 'freevomednafen', ' ', '', [ 'ngp', 'zip' ] )),


 ('wonder swan color', '/home/freevo/roms/wonderswan',
                ('GENERIC', 'freevomednafen', ' ', '', [ 'ws', 'zip' ] )),


('PSone IMG', '/home/freevo/roms/psx1',
                ('GENERIC', '/usr/local/bin/psx-iso', '', '',
[ 'img','bin','iso' ] )) ,

 
('Amiga 500, 1200', '/home/freevo/roms/amiga',
               ('GENERIC', 'run-e-uae',
                '', '', ['adf' , 'zip' ])) ,

('zx spectrum', '/home/freevo/roms/zxspectrum',
               ('GENERIC', 'xspect',
                '', '', ['tzx' , 'tap' ])) ,

('Commodore 64', '/home/freevo/roms/c64',
               ('GENERIC', 'x64',
                '', '', ['d64' , 'zip' , 'tap' , 'z64' ])) ,

('MSX1 and MSX2', '/home/freevo/roms/msx',
                ('GENERIC', '/home/freevo/.freevo/games/msx/run-msx', '', '', [ 'rom' ] )) ,

('Thomson TO8', '/home/freevo/roms/to8/',
                ('GENERIC', '/home/freevo/.freevo/games/to8/run-to8', '', '', [ 'k7' , 'm7' , 'k5' ] )) ,

('Amstrad PCW', '/home/freevo/roms/dos',
               ('GENERIC', 'xjoyce',
                '-a', '', [ 'dsk' ])) ,

('Amstrad cpc 6128', '/home/freevo/roms/amstradcpc',
               ('GENERIC', 'arnold',
                '  -soundplugin 4  -kbdtype 2 -drivea  ', '', [ 'dsk' ])) ,

('Chess', '/home/freevo/.freevo/games/gnomechess',
                ('GENERIC', 'eboard', '', '', [ 'tux' ] )) 


	]

```


Enjoy !!
I can provide the scripts if you would like. Just post

---

