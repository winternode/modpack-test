# WinterPack Alpha - PackWiz

This is a proof of concept for WinterNode's push into Minecraft modpacks, in this case using the [PackWiz](https://packwiz.infra.link/) utility to unify the client and server versions of the pack into one format, and allowing an easy export and sharing of both. 

All processes related to pack management are currently in development, but important points are outlined below. 

## Server-Client differentiation 
When adding a mod to the `mods` folder under a `.toml` file, you can specify the sidedness of each mod, allowing for easy setup of both the client and server setup. 

## Universal sources
Similar to the Modrinth `.mrpack` format, you're able to specify any download source inside of the mod's `.toml` file. This can be used to support both Modrinth and CurseForge by default but also allows for the development and serving of Paper-based packs using Hangar, Modrinth, Github, and Spigot. 

## Auto-update 
The packwiz installer can update a pack by referring to the `pack.toml` file that's hosted on a Github Repo. This can be run on a server or on a 3rd party client like Prism using the startup command shown below.  
  
Windows pre-launch command for Prism/MultiMC  
```shell
sh -c "curl -OL "https://github.com/packwiz/packwiz-installer-bootstrap/releases/latest/download/packwiz-installer-bootstrap.jar" && '$INST_JAVA' -jar packwiz-installer-bootstrap.jar -s client https://raw.githubusercontent.com/winternode/modpack-test/main/pack.toml"
```

Windows single-line for command shell  
```shell
curl -OL "https://github.com/packwiz/packwiz-installer-bootstrap/releases/latest/download/packwiz-installer-bootstrap.jar" && java -jar packwiz-installer-bootstrap.jar -g -s server https://raw.githubusercontent.com/winternode/modpack-test/main/pack.toml
```
  
Both of the above commands install the pack as it is on the GitHub repo. To use another repo or your local version of the pack, you'll need to replace the `https://raw.githubusercontent.com/winternode/modpack-test/main/pack.toml` part of the command. 

## Local Development
The packwiz application is included in the repo for simplicity, and the commands used to add mods can be found [here](https://packwiz.infra.link/tutorials/creating/adding-mods/). To start a local server that serves the `pack.toml` file, run the `packwiz serve` command and change the domain mentioned in the (Auto-update)[#auto-update] section with `http://localhost:8080/pack.toml`. 
