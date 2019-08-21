# Shared image resources for projects in a solution

You can use resource file from another project in your solution if you follow these steps:

1. Create a class library project, let's call it `ResourceLibrary`.
2. Add a `Resx` resource file to the root folder of the project with this name `Resources.Resx`.
3. Open the resource designer and change its *Access Modifier* to `Public`. (It will set its *Custom Tool* to `PublicResXFileCodeGenerator`)
4. Add a few images to the resource designer and save it.

Then in the Windows forms project do the following settings:

1. Add a reference to `ResourceLibrary`.
2. Right click on windows forms project and choose *Add* → *Existing item...*
3. Browse to the `ResourceLibrary` folder and choose `Resources.Resx` file.
4. Click on drop-down arrow of the Open button, and choose ***Add As Link***.
5. Select `Resource.Resx` which has added to windows forms project and choose properties.
5. Set its *Build Action* to `None`
6. Set its *Custom Tool* to a text like `None`
7. Set its *Custom Tool Namespace* to the namespace of the resource in the other assembly: `ResourceLibrary`.
8. Rebuild the project.

Then for all the image properties you can choose the other resource file from drop-down in the *Select Resource* dialog. The code generation will generate correct code for the property and you have a correct build and it works as expected at design-time as well as run-time.

