# n8n: Excel ➜ AI Caption ➜ Instagram + Facebook Publisher

This workflow reads rows from an Excel file, generates post copy with OpenAI, and publishes image/video posts to Facebook Pages and Instagram Business accounts through the Graph API.

## 1) Excel format
Create `/files/social_posts.xlsx` with columns:

- `product`
- `audience`
- `goal`
- `offer`
- `tone`
- `keywords`
- `image_url` (publicly reachable URL)
- `video_url` (publicly reachable URL, optional)
- `publish_to` (`facebook`, `instagram`, or `both`)
- `facebook_page_id`
- `instagram_business_id`
- `facebook_access_token`

## 2) Import workflow
1. In n8n, open **Workflows** ➜ **Import from File**.
2. Import `n8n/excel-to-instagram-facebook-workflow.json`.

## 3) Configure credentials
- Set your OpenAI credential in the **Generate Caption (OpenAI)** node.
- Confirm Graph API version and IDs for Meta endpoints.

## 4) Notes
- Instagram publishing requires a **Business/Creator IG account linked to a Facebook Page**.
- Video publishing to Instagram is configured as Reels (`media_type=REELS`).
- The workflow expects media URLs to be publicly accessible by Meta servers.
- For production, replace per-row tokens with a secure n8n credential or environment variable.

## 5) Optional improvements
- Add `Wait` + status polling for long video processing before `media_publish`.
- Add branch logic to skip image/video nodes when URLs are empty.
- Add schedule trigger instead of manual trigger.
