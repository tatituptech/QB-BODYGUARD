▄︻╦芫≡══--  ⌯⁍
TATITUPTECH BODYGUARD

# QBCore Bodyguard Script

A comprehensive FiveM bodyguard script for QBCore framework that allows players to spawn gang members as bodyguards with automatic weapons who will follow and defend you in combat.

## Features

resources/qb-bodyguard

Code

2. **Add Files**
3. **Update Server Config**
Add this line to your `server.cfg`:
ensure qb-bodyguard
4. **Restart Server**
restart qb-bodyguard
## Usage
### Open Menu
In-game, simply type:
/bodyguard

### Menu Options
- **Spawn Crip Bodyguard** - Spawn a random Crip member
- **Spawn Blood Bodyguard** - Spawn a random Blood member
- **Spawn Vato Bodyguard** - Spawn a random Vato member
- **Spawn Mafia Bodyguard** - Spawn a random Mafia member
- **Spawn Lost Bodyguard** - Spawn a random Lost MC member
- **Dismiss All Bodyguards** - Remove all active bodyguards

### Bodyguard Counter
The menu displays how many bodyguards you currently have spawned (e.g., 2/5)

## Configuration

### Adjust Follow Distance
In `bodyguard.lua`, find this line:
```lua
local followDistance = 0.8 -- Closer follow distance
Lower values = Closer following (minimum 0.1)
Higher values = Further away (try 2.0 for more distance)
Change Maximum Bodyguards
Find this line:

Lua
local maxBodyguards = 5
Change 5 to any number you prefer

Change Weapon Type
In the gangs table, change the weapon field:

Available Automatic Weapons:

weapon_assaultrifle - Standard Assault Rifle (default)
weapon_carbinerifle - Carbine Rifle
weapon_smg - SMG/Machine Pistol
weapon_microsmg - Micro SMG
weapon_combatmg - Combat Machine Gun
weapon_gusenberg - Tommy Gun
Example:

Lua
ballas = {
    models = {...},
    weapon = "weapon_carbinerifle",  -- Change here
    label = "Crip"
}
Adjust Ammo Amount
Find this line in the SpawnBodyguard function:

Lua
GiveWeaponToPed(ped, GetHashKey(gangData.weapon), 500, false, true)
Change 500 to desired ammo amount

Change Bodyguard Health
Find this line:

Lua
SetPedMaxHealth(ped, 300)
SetEntityHealth(ped, 300)
Change 300 to any value (lower = weaker, higher = stronger)

Adjust Combat Range
Find this line in the combat thread:

Lua
if pedDistance < 30 then
Change 30 to your desired combat engagement distance in units

Gang Models
Crip (Ballas)
g_m_y_ballaeast_01
g_m_y_ballaorig_01
g_m_y_ballasout_01
Blood (Family)
g_m_y_famca_01
g_m_y_famdnf_01
g_m_y_famfor_01
Vato (Vago)
g_m_y_mexgoon_01
g_m_y_mexgoon_02
g_m_y_mexgoon_03
Mafia (Mara)
g_m_y_mexgang_01
g_m_y_mexgang_02
g_m_y_mexgang_03
Lost MC
g_m_y_lost_01
g_m_y_lost_02
g_m_y_lost_03
Features Breakdown
Spawning System
Bodyguards spawn in a circle around you
Safe spawn distance prevents clipping
Automatic ground detection
Model loading with timeout protection
Following System
Constant distance checking (every 100ms)
Smooth pathfinding to player
Group membership for togetherness
Never leaves group setting
Combat System
Scans for nearby threats every 500ms
30-unit engagement range
Ignores other bodyguards
Ignores other group members
Only targets hostile NPCs
Cleanup System
Automatically removes dead bodyguards
Removes all on resource stop
Prevents memory leaks
Efficient entity management
Troubleshooting
Bodyguards Not Spawning
Check server console for error messages
Ensure qb-core and qb-menu are running
Verify resource name is qb-bodyguard in server.cfg
Check that models are valid GTA V ped models
Bodyguards Not Following
Increase the followDistance value
Check if player is stuck in objects
Verify no conflicting scripts are running
Bodyguards Not Fighting
Ensure SetPedCombatAbility(ped, 100) is present
Check if nearby peds are marked as hostile
Increase combat range if needed
Performance Issues
Reduce maxBodyguards value
Increase Wait time in combat thread
Remove unused gang types from config
File Structure
Code
resources/
└── qb-bodyguard/
    ├── fxmanifest.lua
    ├── bodyguard.lua
    └── README.md
Dependencies
qb-core - Core framework
qb-menu - Menu system
Console Commands
Spawn Bodyguard
Code
/bodyguard
Chat Notifications
Success Messages
"Crip bodyguard spawned with assault rifle!"
"Blood bodyguard spawned with assault rifle!"
"Vato bodyguard spawned with assault rifle!"
"Mafia bodyguard spawned with assault rifle!"
"Lost bodyguard spawned with assault rifle!"
Error Messages
"Max bodyguards reached!"
"Invalid gang selected!"
"Failed to load gang model!"
"Failed to spawn bodyguard!"
Dismissal
"All bodyguards dismissed"
Console Logging
The script outputs detailed logs for debugging:

[BODYGUARD] Spawning {Gang} with model: {Model}
[BODYGUARD SUCCESS] {Gang} bodyguard spawned!
[BODYGUARD] Removing dead bodyguard
[BODYGUARD] All bodyguards dismissed
[BODYGUARD ERROR] Failed to load model: {Model}
Credits
QBCore Bodyguard Script Created for FiveM & QBCore Framework

License
This script is provided as-is for use with QBCore servers.

Check console logs for error messages
Verify all dependencies are running
Ensure proper file placement
Review configuration settings
Enjoy your bodyguards! 💪
