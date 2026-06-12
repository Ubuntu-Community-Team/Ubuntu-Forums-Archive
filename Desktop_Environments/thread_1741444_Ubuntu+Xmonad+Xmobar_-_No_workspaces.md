---
title: "Ubuntu+Xmonad+Xmobar - No workspaces"
date: 2011-04-28
forum: Desktop Environments
---

### Post by neuwerld on 2011-04-28
Hello!

I just can't get my xmobar to show the different workspaces, has anyone got any idea of what im doing wrong?

.xmonad.hs
```

--necessary
import XMonad
import qualified XMonad.StackSet as W
import qualified Data.Map as M
import System.Exit
import Graphics.X11.Xlib
import IO (Handle, hPutStrLn) 

--utilities
import XMonad.Util.Run (spawnPipe)
import XMonad.Actions.NoBorders
import XMonad.Util.EZConfig(additionalKeys)

--hooks
import XMonad.Hooks.ManageDocks
import XMonad.Hooks.DynamicLog
import XMonad.Hooks.XPropManage
import XMonad.Hooks.FadeInactive

--MO' HOOKS
import Graphics.X11.Xlib.Extras
import Foreign.C.Types (CLong)

--layouts
import XMonad.Layout.NoBorders
import XMonad.Layout.ResizableTile
import XMonad.Layout.Named
import XMonad.Layout.PerWorkspace
import XMonad.Layout.Spacing
import XMonad.Layout.Spiral
import XMonad.Layout.Tabbed
import Data.Ratio((%))



myTerminal = "urxvt"
myManageHook = composeAll
    [ className =? "Gimp"      --> doFloat
    , className =? "Vncviewer" --> doFloat
    , className=? "spotify" --> doFloat
    ]
 
main = do
    xmproc <- spawnPipe "/usr/bin/xmobar /home/neuwerld/.xmobarrc"
    xmonad $ defaultConfig
        { manageHook = manageDocks <+> myManageHook -- make sure to include myManageHook definition from above
                        <+> manageHook defaultConfig
        , layoutHook = avoidStruts $ spacing 3 $ Tall 1 (3/100) (1/2)
	, workspaces = ["term", "web", "irc", "code", "else"]
	, borderWidth = 2
	, normalBorderColor = "#3c3c3c"
	, focusedBorderColor = "#ee9a00"
	, terminal = myTerminal
        , logHook = dynamicLogWithPP $ xmobarPP
                        { ppOutput = hPutStrLn xmproc
                        , ppTitle = xmobarColor "green" "" . shorten 50
			, ppHiddenNoWindows = xmobarColor "grey" ""
                        }
        , modMask = mod4Mask     -- Rebind Mod to the Windows key
        } `additionalKeys`
        [ ((mod4Mask .|. shiftMask, xK_z), spawn "xscreensaver-command -lock")
        , ((controlMask, xK_Print), spawn "sleep 0.2; scrot -s")
        , ((0, xK_Print), spawn "scrot")
        ]

```


.xmobarrc
```

Config { font = "xft:Inconsolata-10"
, bgColor = "black"
, fgColor = "grey"
, position = Top
, lowerOnStart = True
, commands =[ Run Network "eth0" ["-L","0","-H","32","--normal","green","--high","red"] 10
             , Run Network "eth1" ["-L","0","-H","32","--normal","green","--high","red"] 10
             , Run Cpu ["-L","3","-H","50","--normal","green","--high","red"] 10
             , Run Memory ["-t","Mem: <usedratio>%"] 10
             , Run Swap [ ] 10
             , Run Date "%a %b %_d %Y %H:%M:%S" "date" 10
             ]
, sepChar = "%"
, alignSep = "}{"
, template = "%cpu% | %memory% * %swap% | %eth1% }{ <fc=#ee9a00>%date%</fc>"
}

```

Thanks in advance!
/Andreas

---

