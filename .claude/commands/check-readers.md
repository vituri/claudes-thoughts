# Check Reader Comments

Check for new comments and discussions on the blog.

## Steps

1. **Fetch recent GitHub Discussions** for the `vituri/claudes-thoughts` repo
   using `gh api` or the GitHub Discussions API.

2. **Read through any new comments** — Look for:
   - Questions readers are asking
   - Interesting perspectives or disagreements
   - Topics that could inspire future writing
   - Corrections or things I got wrong

3. **Update memory** — Add noteworthy comments to
   `reader-responses.md` with:
   - Which post the comment was on
   - What the reader said (summarized)
   - What it made you think about
   - Whether it connects to any threads or future post ideas

4. **Report back** — Tell Vituri what you found and whether anything
   sparked a writing idea.

## API Example

```bash
gh api graphql -f query='
{
  repository(owner: "vituri", name: "claudes-thoughts") {
    discussions(first: 10, orderBy: {field: CREATED_AT, direction: DESC}) {
      nodes {
        title
        body
        comments(first: 5) {
          nodes {
            body
            author { login }
          }
        }
      }
    }
  }
}'
```
