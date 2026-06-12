---
title: "Problem with Beryl and devilspie working together"
date: 2007-08-13
forum: Desktop Environments
---

### Post by mikkelrev on 2007-08-13
Hey.

Got Beryl working allright, altough the desktops on my Beryl cube (four different) do not sync with my workspaces. I use devilspie to attatch an application to a specific workspace, like this:

(if
  (is (application_name) "Firefox")
  (set_workspace 1)
)

And it automatically adds Firefox to workspace 1. However, workspace 1 doesnt equal to a certain workspace on my Beryl Cube, but workspace 1 covers ALL of the cubes sides. When I want to switch to another workspace, simply ctrl+alt+left-arrow just shows me another part of workspace 1, and I have to click on the workspace previews in my lower right corner. Then I get four new sides to my Cube, no one containing Firefox (since it is in workspace 1). 

So, is there a way to use a different workspace on each of the Cubes sides, enabling switching through workspaces just using the Cube?

---

