# how to release

## :warning: Important notes

  **Check that all cells have their package.json version updated otherwise they won't be updated in k8s**

  - **see `release a cell` from README.md**


## I. Create a Trello card with name `prod release <YYYY-MM-DD>`

1. Attach all cards to that card which are going to be released in production
2. Merge Pull request if not merged yet (in develop) on Github
3. *Optional: add a checklist of any manual steps to be taken during the release*
4. Move the card to `in progress` and trigger the release:

## II. Release cells - Prime the related cells for release 

1. Go on your mashine to branch develop and pull last changes:

    ```bash
    ➜  git:(3466-css-technical-debt) ✗ git checkout develop
    ➜  git:(develop) ✗ git pull origin develop
    ```

3. Prime all cells that was chnged for release

    ```bash
    ➜  git:(develop) ✗ npm -w <cellName> version patch
    ```
    for example: 

    ```bash
    ➜  git:(develop) ✗ npm -w dashboard version patch
    ➜  git:(develop) ✗ npm -w howto version patch
    ➜  git:(develop) ✗ npm -w reports version patch
    ➜  git:(develop) ✗ npm -w backend-crons version patch

    ➜  git:(develop) ✗ git add .
    ➜  git:(develop) ✗ git commit -m "prime for release"
    ➜  git:(develop) ✗ git push origin develop
    ```

## III. Release to production

### #1`Recomended 😃 🚀 🎉 ` Release with Pull Request 

1. Create a **Pull Request** in develop to merge into production branch
2. Add a description to the Pull Request
2. Await for all checks to pass
3. Merge into production
4. Await deployment
5. Create a **Pull Request** to merge production into develop branch
6. Test 

### #2`NOT Recomended!` Release without Pull Request 

  1. merge it into **`production`** branch
  2. push the production branch upstream

### *optional* Execute any manual steps after the release
### Notify  development team in the `prod release <YYYY-MM-DD>` card
### Notify in slack channel about the release and move the card as done