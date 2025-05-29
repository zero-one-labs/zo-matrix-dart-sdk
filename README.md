# 🔧 Customizations in Matrix SDK (Zo Chat)

This project uses a custom Matrix SDK with additional support for Zo-specific features and event types.

## 📦 Custom State Event Types
The following custom state event types have been added and are used within the `client.dart` file of the SDK:

| Event Type          | Description                                                             |
|---------------------|-------------------------------------------------------------------------|
| `zo.config`         | Carries client-side configuration or settings pushed from the server.   |
| `zo.ozone.banner`   | Used to manage banner image within rooms.                               |

## ✉️ Custom Parameters in sendTextEvent (Room.dart)
The `sendTextEvent` method in `Room.dart` has been extended with custom parameters to support advanced Zo Chat functionality.

* ✅ Custom Parameters

| Parameter                     | Type      | Affects                     | Description                                                                     |
|-------------------------------|-----------|-----------------------------|---------------------------------------------------------------------------------|
| `isWebSearchEnable`           | `bool`    | AI & search commands        | Activates web search processing (e.g., web-powered replies).                    |
| `isImageModeEnable`           | `bool`    | Media generation            | Enables image response or generation mode (e.g., prompts for DALL·E or ZoDraw). |
| `isEchoChamber`               | `bool`    | Room behavior customization | Triggers behavior for private, self-looping message scenarios.                  |
| `echoChamberData`             | `String?` | Contextual processing       | Supplies extra data or options for the Echo Chamber scenario.                   |
| `isEchoSquad`                 | `bool`    | Group dynamics              | Supports enhanced group behaviors or multi-user response formats.               |
| `echoSquadData`               | `String?` | Customization               | Additional metadata used for Echo Squad operations.                             |
| `isConversation`              | `bool`    | Threaded command context    | Enables structured, multi-turn conversational commands.                         |
| `selectedConversationMembers` | `String?` | User targeting              | Used to apply commands only to specific members.                                |
| `fromDate`                    | `String?` | Temporal filters            | Filter commands to a date range context.                                        |
| `toDate`                      | `String?` | Temporal filters            | Filter commands to a date range context.                                        |
| `streamId`                    | `String?` | Stream-specific behavior    | Route or scope commands to a particular content stream.                         |

###### 📝 Note:
If you add or modify any custom parameters in the `sendTextEvent` function (e.g., to support new features or command behaviours), you must also update the following:
1. `parseAndRunCommand` method in `room.dart`
2. `CommandArgs` class in `commands_extension.dart`

This ensures consistency and proper handling of command arguments across the system.

This ensures consistency in how command arguments are parsed and handled across the system, especially for custom flags like `isEchoChamber`, `streamId`, or `isImageModeEnable`.
