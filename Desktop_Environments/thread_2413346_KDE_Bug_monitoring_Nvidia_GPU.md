---
title: "KDE Bug monitoring Nvidia GPU?"
date: 2019-02-24
forum: Desktop Environments
---

### Post by davide445 on 2019-02-24
Successfully using [Awesome Widget]("https://arcanis.me/projects/awesome-widgets") (AW) for monitoring various parameters of my PC, want to extend the missing one, the VRAM usage.

Adding a custom script with this code

```
nvidia-smi --query-gpu=utilization.memory --format=csv,noheader
```

is working perfectly from shell, but return this error executed from the widget

```

Tag: custom1
Value: %1(I18N_ARGUMENT_MISSING)
Info: nvidia-smi --query-gpu=utilization.memory --format=csv,noheader
```

Didn't understand if can be a KDE error (i.e. see [this]("https://www.reddit.com/r/kde/comments/6myfqe/weird_activity_error_available_on_1i18n_argument/") post), a AW error or something else.
If there is an easier way to display in a widget the GPU memory utilization I didn't have problem in using something else.

---

